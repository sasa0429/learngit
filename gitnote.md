![1566356966011](C:\Users\XY\AppData\Roaming\Typora\typora-user-images\1566356966011.png)

# 安装 git

下载安装包后，双击进入安装界面，点下一步

Select Components勾选：全选，点下一步

Choosing the default editor used by git（选择当前Git的默认编辑器）：VScode 

adjusting your PATH environment：第二个Git from  the command line and also from 3rd-party software，不建议选第三个

Choosing HTTPS transport backend(加密链接)：use the openSSL library

Configuring the line ending concersions(checkout提交的一些相关模式,回车换行符风格)：checkout windows-style,commit unlx-style line endings

Configuring the terminal emutator to use with git bash（关于命令行的一些内容）:use MinTTY(the default terminal of MSYS2)

Configuring extra options:enable file system catching是否使用文件缓存，enable git credential manager是否使用当前相关授权，证书的相关管理

Configuring  experimental options:enable experimental,built-in add -i/-p

Replacing in-use file:下一步

# 配置

当安装完 Git 应该做的第一件事就是设置你的用户名称与邮件地址。 这样做很重要，因为每一个 Git 的提交都会使用这些信息，并且它会写入到你的每一次提交中，不可更改

~~~git
git config user.name "你的姓名"
git config user.email 你的邮箱
~~~

-- global

通过 `--global` 选项可以设置全局配置信息

```bash
git config --global user.name "你的姓名"
git config --global user.email 你的邮箱
```

> 没加--global：针对某个项目进行
>
> 加了--global：全局配置

检查配置

```bash
# 打印所有config
git config --list
# 打印指定config
git config user.name
```

当结尾出现`:`，按一下`q`键，退出当前预览

创建仓库 - repository

进入希望纳入 git 版本控制的项目目录，使用 `git init` 初始化

```bash
git init
```

该命令将创建一个名为 `.git` 的子目录，这个子目录含有你初始化的 Git 仓库中所有的必须文件，这个目录也是上面我们说的三个区域之一，这个目录也是 Git 保存数据记录的地方，非常重要，如非必要，不要轻易改动

查看隐藏文件：当前文件夹菜单栏-工具-文件夹选项-查看-勾选 显示隐藏的文件、文件夹和驱动器 

查看当前目录下有哪些文件

~~~
$ dir
~~~

清除屏幕：

~~~
$ clear
~~~

乱码问题：

git status 显示乱码

~~~
git config --global core.quotepath false
~~~

终端乱码

菜单-设置-文本-本地/编码

（在当前窗口右键-options-Text-locale选择zh-cn，character set选择utf-8

或修改配置文件（在文件根目录那个.git文件中的config修改）

```
[gui]  
    encoding = utf-8  
    # 代码库统一使用utf-8  
[i18n]  
    commitencoding = utf-8  
    # log编码
[svn]  
    pathnameencoding = utf-8  
    # 支持中文路径
[core]
    quotepath = false 
    # status引用路径不再是八进制（反过来说就是允许显示中文了）
```

如果是尚未纳入追踪的文件，无论在哪个分支都会有提示

合并冲突的时候，比较差异可以用difftool工具

生成 SSH 秘钥

```bash
ssh-keygen -t rsa -C "youremail@qq.com"
```

然后输入生成秘钥的名称，回车，就会生成公私钥文件`id_rsa`和`id_rsa.pub`，可以把它们放到`.git`目录中，默认是放在C盘用户.ssh文件夹中

私钥是本地存储的，公钥是给git、github，作用是在加密的过程中验证的，验证当前提交是否合法



工作流

