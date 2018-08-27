---
title: Working on code generator
layout: post
category: dailyblog
---

### Addressing differences in how components are defined
`Services.jsm` exposes a bunch of components and not all of them are treated equally.
Some of them are exposed only if another class has been registered, or if the current
platform is android. Sometimes we want to expose additional interfaces that we know the component implements for sure and sometimes the component might not be implementing those interfaces. Trying to take care of all of those differences
and passing extra parameters to the `Service` object (in python) will be a nightmare and not very elegant.

For example,
- for `appinfo` component, it might be the case that it does not implement `nsIXULAppInfo` so we will need custom interface exposure for this component
- `crashmanager` component is implemented in JavaScript, so I will have to retrieve it in a different way
- component with contract id `@mozilla.org/childprocessmessagemanager;1` is defined via webidl, so I will have to retrieve it in a different way as well
- `androidbridge` component is only exposed if the platform is android
- component named `policies` is only exposed if `"@mozilla.org/browser/enterprisepolicies;1" in Cc`

So, at least
- [ ] 2 components need to be retrieved in a different way
- [ ] 2 components might need to be exposed only under certain conditions
- [ ] 1 component might not implement an interface we want

So here is my plan
- Abstract out common template code that can be reused between most of the above scenarios
- Modify `Service` class to take the following boolean flags
  - `isCustomServiceGetter` to signify that component retrieval will be custom
  - `isCustomInterfaceDefinition` to signify that querying for interfaces will be custom
  - `isCustomExposure` to signify that the getter will be exposed conditionally
    - this will have to be inserted just before we define a property on the `Services` object
- Allow users to specify custom template generation functions


I was also thinking about how I will eliminate all calls to `Services.jsm` or at least make it so they are forwarded to `Components.Services`. For testing, I could make it so that I comment out all of `Services.jsm` and instead define a global like so
`const Services = Components.Services`. This will allow me to quickly test if all of the Services are working as expected instead of replacing all of them at once and discovering some of them are not working.

Another thing I could do is to create a mochitest of some sort and get each service manually and ensure that I get no errors while retrieving them. This can be an additional level of testing, in case not all of the exposed services are used by JavaScript consumers.

### Components.classes
I need to figure out what exactly the following code bit means
``` js
if ("@mozilla.org/browser/enterprisepolicies;1" in Cc) {
  initTable.policies = ["@mozilla.org/browser/enterprisepolicies;1", "nsIEnterprisePolicies"];
}
```
From [this mdn article](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Language_Bindings/Components.classes)
> Note that `Components.classes` reflects only those component classes that have been previously installed and registered with the component manager using `ContractID`s. If you want to use a class which was only registered with their CID, use `Components.classesByID` instead of `Components.classes` to retrieve it.

How do we check if a certain component has registered with their contract id in C++?

Fast forward to 3 minutes later, somehow, I stumbled upon [XPCOM Reference](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Reference), and from there I found [Core XPCOM functions](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Reference/Core_functions) and there I saw this:
> The `NS_GetComponentRegistrar` function returns a reference to the XPCOM Component Registrar.

Registrar sounds like something that could be useful to me! Looking at the [method overview of nsIComponentRegistrar](https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Reference/Interface/nsIComponentRegistrar) we can see that one of the functions is `boolean isContractIDRegistered(in string aContractID);`. From the documentation,
> This method is used to test for the existence of a class implementing a specific `ContractID`.

I think this is what I was looking for! To double check, I will do a code search for the use of this function to see if it's ever used in C++ code.

Indeed, it is used in several places including [here](https://searchfox.org/mozilla-central/source/dom/webbrowserpersist/WebBrowserPersistLocalDocument.cpp#1223-1229):
```cpp
nsCOMPtr<nsIComponentRegistrar> registrar;
nsresult rv = NS_GetComponentRegistrar(getter_AddRefs(registrar));
MOZ_ASSERT(NS_SUCCEEDED(rv));
if (NS_SUCCEEDED(rv) && registrar) {
   bool result;
   rv = registrar->IsContractIDRegistered(contractID.get(), &result);
   MOZ_ASSERT(NS_SUCCEEDED(rv));
   ...
}
```
