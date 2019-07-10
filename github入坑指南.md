# github入坑指南
* 一、**原理**:
	首先它有一个工作区,一个缓存区和一个版本库.例如新建一个文件,这时它处于工作区,使用git push是不会推到线上版本库的,需使用git add (所要添加的目标文件),这时此文件已处于缓存区,这时使用git commit -m “自己所提交的,需要表述的信息” 给所提交的代码打包,再使用git push提交代码到版本库,这时线上版本库的提交就完成了.
* 二、**词汇/术语**
    `cd`:进入某个目录
    `(target) cd ..`:回到上级目录
    `dir`:列出当前目录下所有文件
    `git init`:初始化一个git版本库
    `git add .`:把当前目录下所有文件都添加到git版本库的缓存区
    (**如果是指定文件，那个"target"就换成指定文件的名字**)
    `git commit -m "first commit "(Custon Name)"`:将缓存区的代码打包并生成备注
    `git remote add origin “仓库地址”`:设置版本库仓库地址
    `git push -u origin master`:把代码提交到版本库的“主线”上
    `git remote -v`:显示当前git仓库地址
    `git remote set-url(设置新地址) origin (要设置的目标地址)`:旧地址改为新版本库地址
    `git pull`:已提交的线上代码拉到本地工作区
    `git clone 目标版本库地址`:复制目标版本库到本地
    `README.md`:描述用文件,也可以用作目录,具体以不同开发环境判断.
    `git status`:查看已修改文件的状态
    `*branch`:分支


* 三、github文件上传教程:
    * 1. `E:\Git>cd ..` 回到git文件夹的上一级目录
    * 2. `E:\>cd PHPEP/RedGreenLight` 进入到目标目录下
    * 3. `E:\PHPEP\RedGreenLight>dir` 列出当前目录下所有文件[**仅限Win，linux&ios用的词是ls,还有一个是ls -al（*可以通过任何第三方的shell命令工具将其简化为ll*）是把隐藏文件在内的所有文件一起列出来，但ls不是**]
    * 4. `E:\PHPEP\RedGreenLight>git init`(**如果该版本库原来有了文件，那么本步骤无需再提**)
    * 5. `E:\PHPEP\RedGreenLight>git add .` 将目标文件夹中所有已修改的文件加入版本库
    * 6.`E:\PHPEP\RedGreenLight>git commit -m "first commit"` 提交代码到git缓存区并起一个名字
    * 7. `E:\PHPEP\RedGreenLight>git remote add origin https://github.com/BeallMLyu/RedGreenLight.git` 添加版本库地址
    * 8. `E:\PHPEP\RedGreenLight>git push -u origin master` 把项目推上版本库主线

    **注:步骤7、8的使用仅限于新建版本库的第一次.之后就是直接地git push(*提交已修改的代码进现有版本库*)
    注2:如果是修改版本库地址，步骤7的add修改成set-url .
    例:git remote set-url origin (*目标版本库地址*)**

* 四、How delete the repository in the web github:
    * 1.find the repository & into it.
    * 2.find that setting.
    * 3.page turn(翻页) to downmost(最下面)-Danger Zone
    * 4.click that “Delete this repository”

