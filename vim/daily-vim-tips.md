---
description: This is a section dedicated to some tips about my daily usage of Vim
---

# Daily Vim tips

### Apply a **macro** to a **Visual mode** selection \(30-01-2020\):

[Link of reference](https://stackoverflow.com/questions/390174/in-vim-how-do-i-apply-a-macro-to-a-set-of-lines)

```bash
# To invoke this you should be in Vim's Ex mode

# initial code
let API_URL = 'https://my-example-api.com'
let ENTITY_PATH = `${API_URL}/entity`

## Step #1:
## Record a macro to put a semicolon(;) at the end of each line
qa A;<Esc>q ## This is the macro, it's stored in the `a` register

## Step #2:
## Visual select the two lines and then(in Ex mode)
:'<,'>norm! @a and let the magic happen

## result code
let API_URL = 'https://my-example-api.com';
let ENTITY_PATH = `${API_URL}/entity`;
```

### Find files inside project's directory \(14-02-2020\)

There are many options when it comes to emulate the **fuzzy search** functionality from IDE's like **VSCode**, **Webstorm**, like **CtrlP**, **fzf.vim**, etc. All of them are great solutions but sometimes **Vim's** search features is all we need.

The trick is quite simple, as usual, before using this please **READ** the **Vim documentation** since messing with this option might not result in what you would expect \(YOU'VE BEEN WARNED\). So, let's continue, when you open **Vim**, enter **:ex mode** and write **set path+=**\*\*.

This options tells **Vim** to set the path where **Vim** will **look for** when using things like **gf**, **:find**, etc. Read **:help path** to find out more about this feature. As you may infer this allows us to search for files inside our project's directory.

This trick is from the great conference [How to do what 90% of plugins do just with Vim](https://app.gitbook.com/@rssanjuan2704/s/knowledge-graph-1/~/drafts/-M04RI2SN5nngs1O62Lh/vim/general#vim-conferences).



