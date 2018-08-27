---
layout: post
title: Sat-Sun, July 21-22, 2018
category: dailyblog
---
### Useful links for Bug XXX
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XTF
  - talks about XTF technologies
- https://developer.mozilla.org/en-US/Firefox/Multiprocess_Firefox/Message_Manager
  - message managers
- http://books.mozdev.org/html/mozilla-chp-8-sect-2.html
  - query interface
-

### More links for learning XPCOM
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XPCOM/Guide/Avoiding_leaks_in_JavaScript_components
- https://developer.mozilla.org/en-US/docs/Mozilla/Tech/XUL/Tutorial/XPCOM_Interfaces
  - talks about XPCOM interfaces
  -

### Bug -
**Things to do**
- Create wrapper
- Add additional interfaces
- Overwrite this getter
- Use resolve hooks

**Creating a wrapper**
- https://searchfox.org/mozilla-central/rev/799c3f49233257bd5e899c4107f65ea394b7ae96/js/xpconnect/idl/nsIXPConnect.idl#232
I need to find a way to wrap the object I created. It does not seem like it is done manually.
  - Do we need to always wrap it?
  -
- Reading this https://searchfox.org/mozilla-central/rev/799c3f49233257bd5e899c4107f65ea394b7ae96/js/xpconnect/src/xpcprivate.h#8-64 and I have a few questions `TODO include a diagram`
  - `nsIClassInfo` why not make all C++ classes implement this interface, so that JS consumers don't have to call `QueryInterface`.
-
