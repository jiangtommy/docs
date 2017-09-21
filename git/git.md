#### git reflog
`git reflog`: check commands history.

#### stage
![stage.jpg](./stage.jpg)
`git add`: add difference to stage   
`git commit`: move difference from stage to branch   
`git diff [file]`: check differences between work dir and stage (not work if file is not in the git control)   
`git diff --cached [file]`: check differences between stage and branch   
`git diff HEAD [-- file]`: check differences between work dir and stage(not work if file is not in the git control)   
#### reset
`git checkout -- file`: 从版本库里的文件替换当前文件   
`git reset HEAD file`: 从暂存区恢复到工作区   
`git reset --hard HEAD file`: 直接从暂存区恢复到最新版本   
#### 远程库
`git remote add origin git@server-name:path/repo-name.git`: 关联远程库   
`git push -u origin master`: 第一次提交时需要用`-u` 会把本地`master`和远程`master`分支关联起来，后续不需要增加`-u`
#### merge
`git merge branch`: 用于合并指定分支到当前分支
#### stash
`git stash apply stash@{0}`: 用于取出指定版本stash
#### tag
`git tag`: 查看所有标签   
`git tag <name>`: 当前版本打标签   
`git tag <name> <commit id>`: 给历史版本打标签   
`git show <tagname>`: 查看指定标签信息   
`git tag -a <name> -m "description" <commit id>`: 创建带有说明的标签，`-a`用于指定标签名，`-m`指定说明文字   
`git tag -d <name>`: 删除指定标签   
`git push origin <tagname>`: 推送指定标签到远程   
`git push origin --tags`: 一次推送所有标签到远程   
删除远程标签：   
```
git tag -d <tagname> // 先删除本地标签
git push origin :refs/tags/<tagname>  //从远程删除
```
