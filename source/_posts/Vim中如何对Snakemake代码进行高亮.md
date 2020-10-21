---
title: Vim中如何对Snakemake代码进行高亮
date: 2020-10-21 15:00:26
tags:
---

Snakemake的官方vim高亮配置[文件](https://raw.githubusercontent.com/snakemake/snakemake/master/misc/vim/syntax/snakemake.vim)下载，将其内容复制到名为`snakemake.vim`的文件中，将其文件复制到`$HOME/.vim/syntax`目录中（如果没有该目录，则用`mkdir`创建）。接着在`$HOME/.vimrc`添加以下命令，使得每次打开*.snk, *.smk和Snakefile文件都以特定方式高亮：

```
autocmd BufNewFile,BufRead Snakefile set syntax=snakemake
autocmd BufNewFile,BufRead *.smk set syntax=snakemake
autocmd BufNewFile,BufRead *.snk set syntax=snakemake
```

在vim中也可以强制显示高亮 ：`:set syntax=snakemake`

注：`vimrc`不需要source，每次添加新的内容保存后退出则自动更新。



### 参考链接：

1. [How do I enable syntax highlighting in Vim for Snakefiles? ]( https://snakemake.readthedocs.io/en/stable/project_info/faq.html#how-do-i-enable-syntax-highlighting-in-vim-for-snakefiles )
2. [ 对于一个自定义的文件类型, 如何使用C, python等语言的关键字高亮方案 ]( https://blog.csdn.net/nankai0912678/article/details/108671782?utm_medium=distribute.pc_relevant.none-task-blog-title-3&spm=1001.2101.3001.4242 )