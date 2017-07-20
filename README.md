# gitlearning
#first time use cmd to complete git

初始化 git目录: git init(是否是空目录都可以， 只要不是已经初始化的)
添加到暂存区： git add [filename]//.表示所有文件（自动识别改变的文件）
提交到（从暂存区提交到分支）： git commit -m 'commit message' //注意提交信息不可以含有关键字
查看改变内容 git diff [filename]
查看提交记录  git log   (全部都放在一行 --pretty=oneline)
版本回退：git reset --hard HEAD~n(回退到前几个版本)
git reset --hard commitID  回退到具体版本
git reflog 查看历史提交命令（其中含有已经提交的commitID）
概念：
工作区working Directory =>所能看到的目录
版本库=>隐藏文件.git   这个目录中有stage（暂存区）。第一个分之master，已经指向版本的HEAD
修改之后不想提交：
git checkout -- filename:回到git add 或者git commit最后一次状态
git reset HEAD filename  撤销提交到暂存区（git add 之后）的内容

commit之后删除工作区文件
1.恢复：git reset --filename
2.真实删除:git rm filename ->git commit -m 'message'
