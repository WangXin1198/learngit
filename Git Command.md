#Git常用命令
[toc]
###指定仓库的用户名和Email地址
>git config --global user.name "Your Name"
>git config --global user.email "email@example.com"

*注意 `git config`命令的 `--global` 参数，用了这个参数，表示你这台机器上所有的Git仓库都会使用这个配置，当然也可以对某个仓库指定不同的用户名和 Email地址。*
___
###创建版本库
>git init   

*将该目录初始化为可管理的仓库，生成.git目录*
___
###把文件添加到版本库
所有的版本控制系统，其实只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等，Git也不例外。版本控制系统可以告诉你每次的改动，比如在第5行加了一个单词“Linux”，在第8行删了一个单词“Windows”。而图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道。
不幸的是，Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动的，前面我们举的例子只是为了演示，如果要真正使用版本控制系统，就要以纯文本方式编写文件。
因为文本是有编码的，比如中文有常用的GBK编码，日文有Shift_JIS编码，如果没有历史遗留问题，强烈建议使用标准的UTF-8编码，所有语言使用同一种编码，既没有冲突，又被所有平台所支持。

1.将文件添加到仓库
>git add readme.txt

2.把文件提交到仓库
>git commit -m "wrote a readme file"
*-m后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。*

为什么Git添加文件需要add，commit一共两步呢？因为commit可以一次提交很多文件，所以你可以多次add不同的文件，比如：

    \$ git add file1.txt
    \$ git add file2.txt file3.txt
    \$ git commit -m "add 3 files."

###时光机穿梭
####查看仓库状态
>git status

查看文件是否被修改，是否有待提交的修改。

####比较版本变动
>git diff readme.txt
省略文件名将输出所有文件变动情况

输出：
>diff --git a/readme.txt b/readme.txt
index 46d49bf..9247db6 100644
--- a/readme.txt
+++ b/readme.txt
@@ -1,2 +1,2 @@
-Git is a version control system.
+Git is a distributed version control system.
Git is free software.

>--- a/readme.txt
+++ b/readme.txt

\---表示变动前的文件
+++表示变动后的文件
>@@ -1,2 +1,2 @@

表示源文件的1-2行与新文件的1-2行有差异
