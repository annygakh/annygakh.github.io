---
layout: post
title: Wednesday, July 10, 2018 - Debug by numbers
category: dailyblog
---
### 9:05 am
While trying to search how to access the 'opener' property from my tests, to ensure it hasn't been set, I came across this test file `dom/tests/browser/browser_noopener.js`. Were my efforts vain? We will find out after I figure out how to run the actual test. So far it has been hanging - the tests run and afterwards the browser window just stays open and no status of the tests is visible. For now I need to move on to a different bug.

### 2:00 pm
- Need to switch back to the clipboard bugs because a review came in.
- Responded to a review  https://reviewboard.mozilla.org/r/252408/
- Reminder of the tests I run when testing the clipboard
    - all of the tests in `testing/web-platform/tests/clipboard-apis` (some of them are manual)
    - mochitest `mach test toolkit/components/extensions/test/mochitest/test_ext_async_clipboard.html`
### 4:00 pm
There was an intern event - we were all to paint Firefox logo on our own canvases.
### 6:00 pm
Looked into the following bug https://bugzilla.mozilla.org/show_bug.cgi?id=1372276 and spoke to a colleague about working on it.
### Much later
Back to working on Bug 1419960. Useful links
- https://developer.mozilla.org/en-US/docs/Mozilla/Browser_chrome_tests
- https://wiki.mozilla.org/Electrolysis/e10s_test_tips#ContentTask


I need to figure out how to access the opener setting on a newly opened tab.
I want to retrieve a `contentWindow` but for some reason after I retrieve the tab, the following does not work `tab.linkedBrowser.contentWindow`.

### A bit later
I searched for `.opener` in the `dom/tests/browser/browser_noopener.js` file and realized I can access the window object if I spawn a new content task in the following way
``` js
    let noopenerTab = gBrowser.tabs[numTabs - 1];
    await ContentTask.spawn(noopenerTab.linkedBrowser, null, async () => {
        ok(!content.window.opener, "Opener should not have been set");
    });
```
