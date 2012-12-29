---
comments: false
date: 2012-10-30 23:58:26
layout: post
slug: 'vim-config-of-pbcopy-pbpaste-on-Mac-OS'
title: ' 文艺MAC用户，Vim中复制粘贴使用 pbcopy 和 pbpaste'
wordpress_id: 108
categories:
- 宅技术
tags:
- 宅技术
---

针对业余 Mac OS 用户，专业者请无视-_-

———–业余的分割线———–

近日非常偶尔非常业余地在配置多个 github 仓库时，恰好需要从 vim 中 copy 配置文件到剪切板，然后IRC发给别人。So，我的做法是先:set nonu, 然后触摸板人肉选择一下（手指已经脱离键盘）-_-，再然后command + c，command + v 发送。

但是，不幸被 [Whyme.Lyu](http://www.douban.com/people/whymelyu/) 围观到，并吐槽，已被鉴定为业余 Mac 用户。

下面介绍正确的操作：使用 pbcopy
pbcopy takes the standard input and places it in the specified pasteboard.

1. 按v进入可视模式
2. 并选择文本
3. 进入命令行模式, 输入 w !pbcopy (将选择的内容写入 pbcopy )  
![](http://ofshellohicy.info/upload/pbcopy.png)
4. 然后可以用 command + v 来粘贴了^_^

——————–命令行使用——————–

![](http://ofshellohicy.info/upload/pbcopy-pbpaste.png)

———————-必杀技———————-

PS: 可以在 ~/.vimrc 里配置这个，以后按F5就会复制到剪切板了

参照：[wiki](http://vim.wikia.com/wiki/In_line_copy_and_paste_to_system_clipboard)
    
    map <F5> :w !pbcopy

或者更高级一点：

    vmap <C-c> y:call system("pbcopy", getreg("\""))
    nmap <C-v> :call setreg("\"",system("pbpaste"))p

至此终于可以随意的复制粘贴，无缝结合。





