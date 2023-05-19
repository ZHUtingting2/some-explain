### push到github常见报错解决方法

#### 一、README文件版本冲突

在push代码到远程仓库时，报了如下的错误：

```
$ git push -u origin master
To https://github.com/11pdg/group-buy.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'https://github.com/11pdg/group-buy.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

有以下几种解决方法：

1、强制push到远程仓库：

```
git push -u origin master -f
```

但是这样会导致远程仓库里的东西丢失，一般不会采用这样的方法，特别是团队开发的时候。

2、push前先将远程仓库pull下来，再进行push：

```
git pull origin master
git push -u origin msater
```

3、创建新的分支：

```
git branch [name]

git push -u origin [name]
```



#### 二、[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)添加远程仓库报错

如果输入$ git remote add origin git@github.com:XXX/XXXX.git 
出现出错信息：fatal: remote origin already exists. 

1、先输入$ git remote rm origin

 

2、再输入$ git remote add origin git@github.com:XXX/XXXX.git

 

3、如果输入$ git remote rm origin 还是报错的话，error: Could not remove config section ‘remote.origin’. 我们需要修改gitconfig文件的内容

 

4、找到你的github的安装路径，..\GitHub\PortableGit_ca477551eeb4aea0e4ae9fcd3358bd96720bb5c8\etc

 

5、找到一个名为gitconfig的文件，打开它把里面的[remote “origin”]那一行删掉就好了！

#### 三、Github提交出现“Everything up-to-date“

向[github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020)提交代码时，执行" git push -u origin main"，提示：
Everything up-to-date
Branch ‘main’ set up to track remote branch ‘main’ from ‘origin’.

解决
1.创建一个新的分支

```c
git branch other    //创建新分支other
```

2.将改动提交到暂存区

```c
git add .
```

3.提交到版本库

```c
git commit -m "描述内容"
```

4.提交到远程仓库

```c
git push origin other
```

5.切换到主分支

```c
git checkout main    //github新建仓分支有master改为了main
```

6.将新建分支合入到主分支上

```c
git merge other
```

7.提交到远程仓库

```c
git push -u origin main
```

8.提交后本地和远程都出现了新分支，删除此无用分支

```c
git branch -d [branchname]    //删除本地分支
```

远程仓显示多了一个分支"other"，删除此无用分支。

![](C:\Users\Administrator\Desktop\some-function\9ad366a4ae0245d1a40b1ae1040d4c46.png)

![](C:\Users\Administrator\Desktop\some-function\dee2b4f7f9f841c3896ee0a4c7f14704.png)

本地与远程仓库恢复干净。