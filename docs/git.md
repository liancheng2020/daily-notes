#### git 代码提交

```git
    git status
    git add .
    git commit -m ''
    git push
```

#### git 判断分支

```git
    git branch
    git branch -a
```

#### git 标签tag相关

```git
    git tag 1.0
    git push origin --tags

    git tag -d 1.0
    git push :refs/tags/1.0
```

#### git 分支创建、关联

```git 
    git checkout -b test  // 创建本地分支test
    git push origin test  // 创建远程分支test
    git branch --set-upstream-to=origin/test // 将本地test分支与远程test分支建立关联
```