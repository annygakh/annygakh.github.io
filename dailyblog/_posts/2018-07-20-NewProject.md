---
layout: post
title: Friday, July 18, 2018
category: dailyblog
---

### Things I could explain
- https://wiki.mozilla.org/XPConnect_object_wrapping


### Things relevant to this new bug
- https://searchfox.org/mozilla-central/source/__GENERATED__/xpcom/build/Services.cpp#390
- https://searchfox.org/mozilla-central/source/js/xpconnect/src/XPCComponents.cpp#416
are these the resolve hooks?
- https://searchfox.org/mozilla-central/source/dom/base/ChromeUtils.cpp#253
  - Will I have to create a class similar to this?

## Guide to understanding XPCOM
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XUL/Tutorial/XPCOM_Interfaces
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Language_bindings/XPConnect
  - https://developer.mozilla.org/en-US/docs/Mozilla/Gecko/Script_security
- Some of the functionality the browser needs to provide is not possible to implement in pure JavaScript. So some of it is implemented in C++ and is exposed to JavaScript and Rust.
- http://books.mozdev.org/html/
  - A book someone made a long time ago. It has a lot of information, and even though some of it is outdated, there are parts that are well documented and are still relevant.
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Guide/Creating_components
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Language_bindings/XPConnect/XPConnect_wrappers

### Trying to figure out what to do
I need to figure out how the newly created Service object will be used by the js consumers. I found some classes where they also create a new object in js and now I need to look for classes where the new component is created using `JS_NewPlainObject` and returned.
- example `ChromeUtils`
  - https://searchfox.org/mozilla-central/source/dom/base/ChromeUtils.cpp#253
    - Is this how I would prepare Services object to be imported?
  - https://searchfox.org/mozilla-central/source/devtools/shared/builtin-modules.js#32
    - And is this how I will be exposing it?
  - Actually, I noticed that `ChromeUtils` is not exactly the same as `Services.jsm` because one can do `ChromeUtils.import("resource://gre/modules/Services.jsm")`
- example `nsFrameMessageManager`
  - Does not apply because it is not created via JS_NewPlainObject
Perhaps I should look for how other `.jsm` files are treated. Maybe there are some that are implemented in C++.

**Update**

Actually, I realized it's okay that `ChromeUtils` is not exactly like `Services.jsm` because I just need an example of how C++ interfaces get exposed to JS code. Perhaps, it is through `webidl`.

**Actually**

It won't work because `ChromeUtils` as an object is already exposed through `webidl`, and it uses low level JS APIs to create a copy of it. But the method that created a copy of itself is defined on an alerady existing object. So it won't work 100% for me.

**3:28 pm**

Perhaps, I will look instead at functions that have the following function declaration
`myFunc(JSContext* aCx, JS::MutableHandleValue aResult)` and see they are exposed.
I found this https://searchfox.org/mozilla-central/source/widget/GfxInfoBase.cpp#1205.
- It seems like I will have to write an `.idl` file.

**4:01 pm**

I don't think I should be creating new `webidl` file because that means I will be creating `Services` object in C++. Furthermore, if I can't really generate a `webidl` file.

**4:54 pm**

I discovered a `Components` object. Per https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Language_Bindings/Components_object
> The `Components` object is the object through which `XPConnect` functionality is reflected into JavaScript.

**5:49 pm**

Success!!! I have managed to create an API in C++ in the `Components` class and expose it
to js. `TODO` This is how I did it.

**Things to do**
- Create wrapper
- Add additional interfaces
- Overwrite this getter
- Use resolve hooks

**To draw**
-
