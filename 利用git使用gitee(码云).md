### 利用git使用gitee(码云)

#### 下载git

> 在git官网下载git。地址：https://git-scm.com/。下载完毕之后直接点击安装。



> 安装成功后在桌面右击可以看到如下两个git提供的两个命令行工具，直接使用第二个。

![image-20230517105039214](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517105039214.png)



#### 使用gitee

> 在gitee上注册账号并登陆

> 配置公钥（不然后面每次上传文件到远程仓库都需要用户名密码验证，就很麻烦）

​		1.设置==>SSH公钥，点击怎样生成公钥，会有详细步骤。

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517105637746.png" alt="image-20230517105637746" style="zoom: 67%;" />

​		2.生成SSH公钥（这里的邮箱可以随便写一个）。命令：

```
ssh-keygen -t ed25519 -C "xxxxx@xxxxx.com"  
# Generating public/private ed25519 key pair...
```

​		3.用文档打开对应路径下的公钥。（eg:C:\Users\Administrator\.ssh）

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517110430303.png" alt="image-20230517110430303" style="zoom:67%;" />

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517110514459.png" alt="image-20230517110514459" style="zoom:67%;" />

将这串标识复制粘贴到gitee中，标题可以随便取，然后点击确定

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517110734032.png" alt="image-20230517110734032" style="zoom: 80%;" />

​		

**PS：如何判定是否添加成功？**

在终端（Terminal）中输入：

```
ssh -T git@gitee.com
```

![image-20230517145647970](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517145647970.png)

> 新建仓库

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517145926961.png" alt="image-20230517145926961" style="zoom:67%;" />

​		1.第一步git全局设置（只需要配置一次），命令：

```
git config --global user.name "is枳橘子"
git config --global user.email "2521095558@qq.com"
```

![image-20230517150314742](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517150314742.png)

​		2.远程仓库：

​			下载仓库=>下载命令使用ssh地址（还有一种是https），命令如下（不同仓库这个地址不一样）：

![image-20230517150545699](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517150545699.png)

```
git clone git@gitee.com:isZiJuzi/some-function.git
```

​			![image-20230517150910169](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517150910169.png)

​		上传仓库=>在该文件夹里放置一些文件。上传时一定要进入该文件夹。有两种方式，1是cd some-function/

​		(我这里文件夹是some-function)。2是进入该文件夹右击打开git命令行。

![image-20230517151813055](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517151813055.png)

​		接下来执行上传命令（双引号内是自定义内容，为该文件的描述）：

```
git add .
git commit -m "一些环境配置、方法"
git push origin master
```

![image-20230517152845769](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230517152845769.png)







