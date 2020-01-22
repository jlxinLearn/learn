# 学习ruby开发网站

## 命令行

>一切的开始就是命令行

命令行的组成部分

+ 提示
+ 命令
+ 选项
+ 参数
+ 光标

```bash
echo hello
echo "hello"
echo 'hello'
```

使用**man**命令可以查看手册

```bash
man echo
```

```bash
man man
```

清空命令行

```bash
clear
```

`clear`的相应的快捷键是<kbd>Ctrl</kbd>和<kbd>L</kbd>

退出当前的任务

```bash
exit
```

常用的快捷键

|快捷键|作用|
-|-|
<kbd>Ctrl</kbd>-<kbd>C</kbd>|推出当前的线程|
<kbd>Ctrl</kbd>-<kbd>A</kbd>|移动到一行的开头|
<kbd>Ctrl</kbd>-<kbd>E</kbd>|移动到一行的结尾|
<kbd>Ctrl</kbd>-<kbd>U</kbd>|删除到开头|
<kbd>Ctrl</kbd>-<kbd>L</kbd>|清理整个终端|
<kbd>Ctrl</kbd>-<kbd>D</kbd>|退出|

使用命令行进行**文件操作**

使用`>`进行重定向的操作
使用`>>`表示进行追加的操作
使用**cat**显示文件的内容
使用**diff**比较不同的两个文件

```bash
diff 1.txt 2.txt
```

最常用的命令**ls**列出当前文件夹下的所有文件和目录

ls 文件名/目录名 展示想要的文件或目录/不存在会相应的提示

```bash
ls foo
```

常用的选项

-rtl 按照使用的时间排序
-d 只显示目录

```bash
ls -l *.txt
ls -rtl
ls -a
ls -d
```

**touch**创建一个空的文件

```bash
touch foo
```

**cd**切换目录

文件改名

```bash
mv test test.txt
```

文件夹改名

```bash
mv foo/ bar/
```

文件夹的拷贝

拷贝文件夹里面的文件和文件夹本身

```bash
mkdir foobar/
cp -r ../text_files .
```

只拷贝文件
```bash
cp ../text_files/* .
```

文件拷贝

```bash
cp 1.txt 1c.txt
```

删除文件

```bash
rm 1c.txt
rm -f *.txt
```

现在文件

检查是否安装可curl

```bash
which curl
```

```bash
curl -OL https://cdn.learnenough.com/sonnets.txt
curl -I https://www.learnenough.com
```

使用**head**和**tail**查看文件

```bash
head sonnets.txt
tail sonnets.txt
```

使用**wc**对文件进行计数

```bash
head sonnets.txt > sonnets_head.txt
wc sonnets_head.txt
```

使用管道

```bash
head sonners.txt | wc
```

使用**more**和**less**查看文件的内容

```bash
less sonnets.txt
```

使用**less**可以通过\\进行搜索,使用**n**查找下一个，使用**N**查找上一个，使用**G**移动到文件的末尾，使用**1G**移动到文件的开头

使用**grep**查找文件中的内容

```bash
grep rose sonnets.txt
```

递归查找相应的文件夹

```bash
grep -r sesquipedalian text_files
```

忽略大小写

```bash
grep -i rose sonnets.txt | wc
```

显示进程表

```bash
ps aux
```

```bash
ps aux | grep spring
```

通过**pid**停止想要的进程

```bash
kill -15 12241
```

杀死所有的满足特定的每次的进程

```bash
pkill -15 -f spring
```

使用**sudo**提升用户的权限

```bash
sudo touch /opt/foo
```

使用**mkdir**创建文件夹

```bash
mkdir text_files
```

使用**mv**移动文件

```bash
mv *.txt text_files/
```


使用**cd**切换目录

```bash
cd text_files/
```

+ ..表示父目录
+ ~表示家目录
+ -表示上一次的目录
+ .表示当前的目录

**绝对路径**和**相对路径**

```bash
cd ~
cd ../../a.txt
```

不接参数表示的是转到用户的家目录

```bash
cd
```

使用**pwd**获得当前的目录

```bash
pwd
```

使用**find**查找文件

```bash
find . -name '*.txt'
```

使用默认程序打开当前文件

```bash
open .
```

运行多个程序

```bash
./configure &&make && make install
```

使用**rmdir**删除空的文件夹

```bash
rmdir dir
```

使用**rm -rf**删除文件夹

```bash
rm -rf dir
```



## git

安装

在linux中一般都自带了git

```bash
which git
```

安装以后对git进行全局的设置

```bash
git config --global user.name "jlxingbs"
git config --global user.email "jlxingbs@gmail.com
```

使用git初始化仓库

```bash
mkdir -p repos/website
cd repos/website
git init
```

使用commit提交

```bash
touch index.html
git status
git add -A
git status
git -m commit "Initialize repository"
```

使用log查看日志信息

```bash
git log
```

使用**哈希**值表示相应的**commit**信息

观察文件之间的变化

```bash
echo 'hello world' > index.html
git diff
```
`git diff`表示的是当前的文件和最后一次的commit一次的文件之间的不同

```bash
git commit -a -m "Add content to index.html"
```

>-a只是提交有变化的文件，增加的文件使用`git add -A`忍让非常重要

建议使用**commit**的时机根据实际情况而定，但是在有相当多的变化的时候建议commit它

打开文件`index.html`，修改为以下的内容

```html
<h1>hello,world</h1>
```

```bash
git commit -am "commit a tag"
```

打开文件`index.html`，修改为以下的内容


```html
<!DOCTYPE html>
<html>
    <head>
        <title></title>
    </head>
    <body>
        <h1>hello world</h1>
        <p>call me</p>
    </body>
</html>
```

```bash
git commit -am "Add some HTML structrue"
```

如何进行远程的push

```bash
git pull origin master --allow-unrelated-history
git remote add origin https://github.com/jlxinLearn/notes
git push -u orgin master
```

`-u`表示我们表示使用**GitHub**作为上游的仓库，当我们使用`git pull`的时候我们会我们会自动的下载所有的改变

**创建.gitignore文件**

1. #为注释
2. 目录的写法是绝对路径和相对路径 绝对路径以/开头 相对路径以./开头
3. \*为表示匹配任意一个字符的通配符
4. \[\]表示匹配单个字符
5. !表示不忽略匹配到的文件和目录

创建一个新的分支

```bash
git checkout -b about-page
```