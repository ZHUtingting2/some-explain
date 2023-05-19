### vscode 配置 gitbash 终端，并设置为默认

#### 一. 使gitbash生效

1. 打开vscode
2. 文件->首选项->设置，打开设置（或者点击左下角的设置图标）
3. 搜索`shell windows`
4. 点击在`setting.json`中编辑

![image-20230518170356897](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518170356897.png)

在[vscode](https://so.csdn.net/so/search?q=vscode&spm=1001.2101.3001.7020)升级后,在默认的终端配置文件中显示的是`"Git Bash"`,因为中间有空格所以无法识别。

5.可以在中间增加短横杠`"-"`,更改成`"Git-Bash"`。并删除原内容，增加`"path"`，值为`bash.exe`所在目录。
！！！需要是`bin`目录下的`bash.exe`！！！

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518170610220.png" alt="image-20230518170610220" style="zoom:67%;" />



![image-20230518170508721](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518170508721.png)



6.此时点击终端->新建终端，就能看到`Git-Bash`被添加到终端列表中。

![image-20230518170739948](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518170739948.png)

#### 二. 将gitbash设置为默认终端

1. 打开vscode

2. 文件->首选项->设置，打开设置

3. 搜索shell windows

4. 在`Terminal › Integrated › Default Profile: Windows`中选择`Git-Bash`即可设置其为默认终端

   ![image-20230518170940808](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20230518170940808.png)