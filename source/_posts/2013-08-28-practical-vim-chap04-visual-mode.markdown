---
layout: post
title: "practical vim --chap04 Visual Mode"
date: 2013-08-28 15:38
comments: true
categories: vim_emacs
---
1. Vim’s Visual mode allows us to define a selection of text and then operate upon it.

2. ways to enabling visual modes:
```
v Enable character-wise Visual mode
V Enable line-wise Visual mode
<C-v> Enable block-wise Visual mode
gv Reselect the last visual selection
```


3. the 'gv' command isreselects the range of text that was last selected in Visual mode. No matter whether the previous selection was character-wise, line-wise, or block-wise, the gv command should do the right thing. The only case where it might get confused is if the last selection has since been deleted.



4. if there is a html tag, like "<a href="#">three</a>", type vit in normal mode, will get you put your cursor into the 'h' character of the word "three". vit means "visually select inside the tag"



