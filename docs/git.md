#### git 代码提交

```
    git status   // 判断已修改还未提交的文件
    git add .    // 将修改的文件提交到暂存区
    git commit -m ''  // 将修改的文件由暂存区提交到仓库
    git push  // 推送到远程仓库
```

#### git 判断分支

```
    git branch     // 查看本地分支
    git branch -a   // 查看本地与远程所有分支
    git branch -D dev  // 删除本地dev分支
    git push origin --delete dev  // 删除远程dev分支
```

#### git 标签tag相关

```
    git tag 1.0  // 新建一个tag
    git push origin --tags  // 提交所有tag

    git tag -d 1.0  // 删除本地的tag
    git push :refs/tags/1.0  // 删除远程的tag
```

#### git 分支创建、关联

```
    git checkout -b test  // 创建本地分支test
    git push origin test  // 创建远程分支test
    git branch --set-upstream-to=origin/test // 将本地test分支与远程test分支建立关联
```

#### git 修改commit

```
    git commit --amend   // 修改最近一次的commit信息
```


#### git 撤销commit

```
    git reset --soft HEAD^    // 撤销上一次的commit，不撤销add
    git reset --hard HEAD^    // 撤销上一次提交的commit和add
    git reset --hard HEAD～2  // 撤销前两次提交的commit和add
```