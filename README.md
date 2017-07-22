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
1.所有空行或者以注释符号 ＃ 开头的行都会被 Git 忽略。
2.可以使用标准的 glob 模式匹配。
3.匹配模式最后跟反斜杠（/）说明要忽略的是目录。
4.要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。

#### glob模式要点:

1.*:任意个任意字符,
2.[]:匹配任何一个在方括号中的字符,
3.?:匹配一个任意字符，
4.[0-9]:匹配字符范围内所有字符

作者：iOSReverse
链接：http://www.jianshu.com/p/8c0d262e49a6
來源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```
.DS_Store
node_modules/
npm-debug.log
yarn-error.log
*.txt
```




