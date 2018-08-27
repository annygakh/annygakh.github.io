---
layout: post
title: Working on bugs and figuring out Arcanist
category: dailyblog
---
### Morning
Sent out a bunch of patches with changes made according to the review comments.

Trying to figure out how `arc diff` works.

#### How to send a single commit from the past for review via arcanist
Suppose you have the following commits (latest first)
```
AAA - Bug AAA
BBB - Bug BBB
CCC - Bug CCC
```
and you want to submit only commit B for the review.

You need to
- checkout commit `BBB`
- `$ arc diff HEAD^` to submit the review

If you want to preview what you are about to submit you can do `$ arc diff --preview HEAD^`

#### How to pull a changeset from try if you are using git cinnabar
- I created a new local branch
- `git cinnabar fetch hg::https://hg.mozilla.org/try <changeset>`
- Per https://stackoverflow.com/a/23960663, I did
`git config core.ignorecase true`
- `git rebase FETCH_HEAD`

### Evening
Realized that browser_noopener* tests were hanging because they expected a new window to be created, but the bug fix was to make it so a new tab would open instead. So I modified the tests and now the tests pass. Success!
