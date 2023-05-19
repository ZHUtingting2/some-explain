### 利用git使用gitHub

#### 一.下载仓库

1.建立一个文件夹，并用这个文件夹存储接下来克隆（down）的文件，右击打开git命令行，命令如下：

```
git clone https://github.com/thx/gogocode.git
```

![image-20230518154458394](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518154458394.png)

后面的地址为gitHub中仓库地址

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518154439556.png" alt="image-20230518154439556" style="zoom:67%;" />

> PS：使用Download ZIP直接下载，只是单纯的下载了一个文件夹，和git没有关系，即以后对该文件夹做的操作和更改只是存在于本地，那么如何让这个文件夹在于git仓库连接上呢？那么首先就要对该文件夹进行初始化。
>
> 初始化仓库：git init     初始化完毕后会出现 .git 这个隐形文件夹

![image-20230518155444197](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518155444197.png)

#### 二.上传仓库

1.此处是结合vscode来讲解代码提交（主要目的是vscode中有更简单，一键操作的方式...）

​	在文件夹中，点击 .git 并右击，通过vscode打开（也可以用git命令行，只不过vscode对git有集成，方便在编辑器内使用命令）。

> **PS：**如果打开的终端面板不是Git的终端配置，原因：下载**安装Git时没有安装在C盘默认路径**（一直下一步的傻瓜式安装），安装到D盘或者其他盘了，导致vscode找不到（可在设置中，打开settings.json文件将Git Bash 集合下，更改path，具体操作见【vscode 配置 gitbash 终端，并设置为默认】）

![image-20230518190836228](C:\Users\Administrator\Desktop\some-function\image-20230518190836228.png)

​	将这个文件加入暂存区，如果需要加入整个文件，那么将-A换成具体的文件名。以下两种命令书写都可以

```
git add -A
```

```
git add .
```

------

> PS：如果在输入命令行回车后，终端显示出“warning: LF will be replaced by CRLF”警告。原因是：LF和CRLF都是换行符，在各操作系统下，换行符是不一样的。

```
在Git中，可以通过以下命令来显示当前你的Git中采取哪种对待换行符的方式

$ git config core.autocrlf

此命令会有三种输出：true、false、input

true：将add的所有文件视为文本文件，将结尾的CRLF转换为LF；checkout时会将文件的LF转换为CRLF格式。使用linux平台建议使用，

false：不做任何改变。只在windows下，建议使用

input：add时，将CRLF转换为LF；checkout时还是LF。windows不建议使用
```

![image-20230518194857068](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518194857068.png)

------

执行完之后，文件会从“更改”这个工作区，移动到“暂存的更改”这个区域。然后提交到仓库，执行命令如下：

```
git commit -m "这是文件描述信息，可以随便填"
```

![image-20230518200537215](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518200537215.png)

以上，代表已经提交成功！！！

**简单操作**：直接点击项目后面“+”号，添加到暂存区，然后在master按快捷提交

![image-20230518201124902](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518201124902.png)

#### 三.查看提交历史

```
git log
```

![image-20230518201349742](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518201349742.png)

利用插件也可以直接了当查看显示历史记录

![image-20230518202340768](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518202340768.png)

![image-20230518202424765](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518202424765.png)

#### 四.更改文件内容

1.把这个文件夹里面的内容进行修改，会看到“更改”工作区又出现了一个带M的文件

![image-20230518202832766](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518202832766.png)

2.回滚历史修改（相当于将本次所有更改撤销）：

```
git checkout README-cn.md
```

![image-20230519110715006](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519110715006.png)

**简单操作：**可以直接点击工作区文件，点击“撤回”图标

3.提交后对文件在进行撤销（历史记录最新1次提交的文件，冒尖后面加上1）

```
git reset HEAD^1
```

![image-20230519112132931](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519112132931.png)

简单操作：选中需要撤回的历史记录，undo commit

![image-20230519112023841](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519112023841.png)

#### 五.分支

让不同的人进行分工、隔离开发项目，开发后又能对这些分支进行汇合在一起。

```
//以当前分支为基础新建分支，testpro。
git checkout -b testpro

//切换到主分支
git checkout master

//列举所有的分支
git branch

//合并分支,将testpro合并到master，注意合并时要切换到master路径
git merge testpro

//查看有哪些分支
git branch
```

1.创建分支：

![image-20230519135516717](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519135516717.png)

这样切换到不同分支进行代码修改时，就不会相互产生影响了。接下来将分支合并到主节点

2.将分支合并到主节点：

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519141348967.png" alt="image-20230519141348967" style="zoom:150%;" />

3.合并不同分支到master：

由于我创建了两个分支，并且在同一一文件名中、同一位置更改了代码，那么在合并时就会产生冲突。

![image-20230519141838642](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519141838642.png)

![image-20230519142224713](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519142224713.png)

如果没有能力对此次冲突的代码进行合并，那么可以放弃此次合并：

```
git merge --abort
```

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519142605290.png" alt="image-20230519142605290" style="zoom:150%;" />

4.查看分支：

查看当前节点有哪些分支

```
git branch
```

![image-20230519142850489](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519142850489.png)

5.删除分支：

```
git branch -D testpro
```

![image-20230519143327082](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519143327082.png)

#### 六.git与gitHub远程仓库

1.新建一个仓库

![image-20230519144022793](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519144022793.png)

新建仓库成功后，会有很多命令告诉你怎么去操作这个仓库

![image-20230519144137974](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519144137974.png)



2.添加文件到仓库：

添加一个已经存在的git文件到这个新仓库，执行命令如下：

```
git remote add origin git@github.com:ZHUtingting2/gogocode-copy.git
git branch -M main
git push -u origin main
```

![image-20230519153119431](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519153119431.png)

> 推荐使用SSH，使用Https时，在执行完 git push -u origin main 后会进行账号验证，比较慢。

------

出现了提交失败的提示，以下是解决办法：

1、在git中执行**git config --global --unset http.proxy**和**git config --global --unset https.proxy**

![image-20230519154025562](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519154025562.png)

2、在cmd下执行**ipconfig/flushdns** 清理DNS缓存

![image-20230519154047094](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519154047094.png)

3、重新执行**git clone https://github.com/…/.git/’** 即可

![image-20230519154116903](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519154116903.png)

------

解决完毕之后重新连接仓库，在进行提交，这样就成功啦！

![image-20230519154228716](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519154228716.png)

![image-20230519154329803](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230519154329803.png)

3.推送和拉取分支：

```
//推送当前分支最新版本到远程
git push

//拉取远程分支最新的提交到本地
git pull
```

