# gitlearning

#### 初始化 git目录: git init(是否是空目录都可以， 只要不是已经初始化的)
#### 添加到暂存区： git add [filename]//.表示所有文件（自动识别改变的文件）
#### 提交到（从暂存区提交到分支）： git commit -m 'commit message' //注意提交信息不可以含有关键字
#### 查看改变内容 git diff [filename]
#### 查看提交记录  git log   (全部都放在一行 --pretty=oneline)
#### 版本回退：git reset --hard HEAD~n(回退到前几个版本)
#### git reset --hard commitID  回退到具体版本
#### git reflog 查看历史命令（其中含有已经提交的commitID）
#### 概念：
#### 工作区working Directory =>所能看到的目录
#### 版本库=>隐藏文件.git   这个目录中有stage（暂存区）。第一个分之master，已经指向版本的HEAD
#### 修改之后不想提交：
#### git checkout -- filename:回到git add 或者git commit最后一次状态
#### git reset HEAD filenme  撤销提交到暂存区（git add 之后）的内容
#### commit之后删除工作区文件
#### 1.恢复：git reset --filename
#### 2.真实删除:git rm filename ->git commit -m 'message'
####  创建并切换分支：git checkout -b branchname
#### -b表示切换，也可以分别操作
#### git branch branchname 来创建分支
#### git checkout branchname 切换分支
#### git branch -》查看当前分支（会列出所有分支）
#### git merge branchname  将某个分支合并到当前分支
#### git branch -d branchname 删除分支
#### git branch -D branchname强制删除（比如没有合并的分支）
#### 有冲突的时候，可以强制禁用Fast forward,但是会在merge的是候产生一个commit ，所以在写的时候要写上提交参数
#### git merge --no-ff -m 'new commit message' branchname
#### 查看分支历史：git log --graph --pretty=oneline --abbrev-commit
#### git stash 将当前工作区内容暂存起来。
#### 1.git stash pop恢复内容并删除stash
#### 2.git stash apply + git stash drop (手动删除)
#### 查看stash： git stash list
#### git stash apply stash@{0}（恢复指定stash中的内容）
#### git remote 查看远程库信息
#### git remote -v 查看详细信息
#### 远程库默认名称为origin 
#### 推送到远程 git push origin branchname
#### 打标签  
#### git tag tagID(在当前commitid上打标签)
#### 在历史记录上， 先查询历史记录提交
#### git log --pretty=oneline --abbrev-commit
#### 然后找到对应的commitID  ->git tag tagID commitID
#### 查看tag标签  git tag(按照字符顺序列出)
#### 查看标签详细信息 git show tagID
#### git tag -a <tagname> -m "blablabla..."可以指定标签信息；
#### 编写.gitignore文件可以忽略某些文件
#### 忽略操作系统自动生成的文件，比如缩略图等；
#### 忽略编译生成的中间文件、可执行文件等，也就是如果一个文件是通过另一个文件自动生成的，那自动生成的文件就没必要放进版本库，比如Java编译产生的.class文件；
#### 忽略你自己的带有敏感信息的配置文件，比如存放口令的配置文件。
#### .gitignore文件用于忽略文件,其规范如下
##### 1.所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
##### 2.可以使用标准的 glob 模式匹配。
##### 3.匹配模式最后跟反斜杠（/）说明要忽略的是目录。
##### 4.要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。

#### glob模式要点:

##### 1.*:任意个任意字符,
##### 2.[]:匹配任何一个在方括号中的字符,
##### 3.?:匹配一个任意字符，
##### 4.[0-9]:匹配字符范围内所有字符

```
.DS_Store
node_modules/
npm-debug.log
yarn-error.log
*.txt
```
git push 使用本地的对应分支来更新对应的远程分支。

$ git push <远程主机名> <本地分支名>:<远程分支名>

注意: 命令中的本地分支是指将要被推送到远端的分支，而远程分支是指推送的目标分支，即将本地分支合并到远程分支。 
如果省略远程分支名，则表示将本地分支推送与之存在”追踪关系”的远程分支(通常两者同名)，如果该远程分支不存在，则会被新建。

$ git push origin master

上面命令表示，将本地的master分支推送到origin主机的master分支。如果后者不存在，则会被新建。 
origin是一个远程厂库地址。

如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支，这条命令是删除远程master分支。

$ git push origin :master
  等同于
$ git push origin --delete master

上面命令表示删除origin主机的master分支。

如果当前分支与远程分支之间存在追踪关系（即分支名相同），则本地分支和远程分支都可以省略。

$ git push origin

上面命令表示，将当前分支推送到origin主机的对应分支。

如果当前分支只有一个追踪分支，那么主机名都可以省略。

$ git push

如果当前分支与多个主机存在追踪关系，则可以使用-u选项指定一个默认主机，这样后面就可以不加任何参数使用git push。

$ git push -u origin master

上面命令将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了。

不带任何参数的git push，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用git config命令。

$ git config --global push.default matching
 或者
$ git config --global push.default simple

还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用–all选项。

$ git push --all origin

上面命令表示，将所有本地分支都推送到origin主机。

如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做git pull合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用–force选项。

$ git push --force origin

上面命令使用–force选项，结果导致在远程主机产生一个”非直进式”的合并(non-fast-forward merge)。除非你很确定要这样做，否则应该尽量避免使用–force选项。

最后，git push不会推送标签(tag)，除非使用–tags选项。

$ git push origin --tags

git pull 获取并合并其他的厂库，或者本地的其他分支。

git pull 与 git push操作的目的相同，但是操作的目标相反。命令格式如下：

git pull <远程主机> <远程分支>:<本地分支>

例如：

git pull origin master:my_test

上面的命令是将origin厂库的master分支拉取并合并到本地的my_test分支上。

如果省略本地分支，则将自动合并到当前所在分支上。如下：

git pull origin master

注：如果你想参与github上的一些优秀的项目，则下面提供一个通用的例子： 
首先，需要一个github的账号，并fork一个你感兴趣的repository。 
下面描述过程中会涉及两个远程主分支，为了很好的区别，我们把fork出来的主分支称为远程A repository，本fork的分支称为远程B repository

$git clone <远程Arepository> #克隆你fork出来的分支

$git remote add <远程Brepository标签> git@github.com:XXXX/ceph.git #添加远程Brepository标签

$git pull <远程B厂库标签> master:master  #从远程Brepository的master分支拉取最新objects合并到本地master分支

$git checkout YYYY #切换到要修改的分支上

$git branch develop; git checkout develop #在当前分支的基础上创建一个开发分支，并切换到该分支上，你将在该分支上coding

coding...... #在工作区coding

$git add .#将修改保存到索引区

$git commit -a #将修改提交到本地分区

$git push origin my_test:my_test #将本地分支my_test提交到远程A repository的my_test分支上

然后在github web界面上将my_test分支合并到你需改的远程B repository 分支上。等待管理员review，如果有问题，就继续在develop分支当修改，并commit –amend，在之前的commit上修改。知道被meger。



