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





