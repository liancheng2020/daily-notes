#### git 代码提交

```
    git status
    git add .
    git commit -m ''
    git push
```

#### git 判断分支

```
    git branch
    git branch -a
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

#### git 撤销commit

```
    git reset --soft HEAD^    // 撤销上一次的commit，不撤销add
    git reset --hard HEAD^    // 撤销上一次提交的commit和add
    git reset --hard HEAD～2  // 撤销前两次提交的commit和add
```