Git 知识点整理

- 什么是版本控制

- 什么是Git

- - 人工版本控制器
  - 版本控制工具
  - 常见版本控制工具

- 如何工作

- - Git文件的生命周期

  - 状态

  - - 未追踪        Untracked
    - 已修改        modified
    - 已暂存        staged
    - 已提交        committed

  - 区域

  - - 工作目录
    - 暂存区域

- 安装

- 配置

- - --global

  - - git config --global user.name
    - git config --global user.email

  - 检查配置

  - - git config --list
    - git config user.name

- 创建本地仓库  - repository

- - git init

- 工作流和基本操作

- - 查看工作区文件状态

  - - git status

  - 内容从工作区添加到暂存区

  - - git add

    - - git add .

  - 从暂存区提交到本地Git仓库

  - - git commit

    - - 提交备注         

      - - git commit

      - 修改默认编辑器

      - - git config core.editor notepad
        - git config --global core.editor "code  --wait"

      - 单行备注

      - - git commit -m 备注信息

  - 查看提交日志

  - - git log

    - - git log --oneline

  - 回退

  - - git reset

    - 回退版本

    - - git reset --hard HEAD/commitID

    - 撤销暂存区内容

    - - git reset HEAD/commitID 文件
      - git checkout -- 文件

  - 删除文件

  - - git rm 文件

    - 只删除git仓库文件

    - - git rm --cached 文件

  - 追加提交

  - - git commit --amend -m 提交备注

  - 比较

  - - 工作区和暂存区

    - - git diff 文件

    - 暂存区和仓库

    - - git diff git diff --cached [commitId] 文件

    - 工作区和仓库

    - - git diff HEAD/commitId 文件

    - 仓库不同版本

    - - git diff commitId1 commitId2

- 问题：乱码

- - 中文乱码

  - git status 乱码

  - - git config --global core.quotepath false

  - 终端乱码

  - - 菜单  -> 设置 -> 文本 -> 本地 / 编码

- 分支

- - 查看分支

  - - git branch

  - 创建分支

  - - git branch 分支名

  - 切换分支

  - - git checkout 分支名

  - 创建并切换分支

  - - git checkout -b 分支名

  - 分支合并

  - - git merge 分支名

    - 查看已经合并的分支

    - - git branch --merged

    - 查看未合并的分支

    - - git branch --no-merged

  - 删除分支

  - - git branch -d 分支名
    - git branch -D 分支名 强制删除

  - rebase

  - - ~  纵向 与  ^横向
    - rebase  操作

  - 合并冲突

  - - 查看冲突文件 - 修复冲突内容 - 提交

  - 版本标签

  - - git tag 版本号

    - 特定历史版本

    - - git tag -a v1.0.0 HEAD/commitId

- 协同开发

- - github

  - - 注册账号

    - 生成SSH密钥

    - - ssh-keygen -t rsa -C "email@qq.com"

    - 添加代理

    - - eval $(ssh-agent -s)

    - 添加私钥

    - - ssh-add 私钥路径

    - 在github上添加公钥

    - - 个人中心 -> 设置  -> ssh -> 添加

    - 测试

    - - ssh -T git@github.com

  - github远程

  - - 链接

    - - git remote add origin         git@github.com:githubusername/projectname.git

    - 提交（同步）远程

    - - git push -u origin master
      - git push origin master

    - 远程分支

    - - 提交到远程（分支）

      - - git push origin [本地分支名称]:[远程分支名称]

      - 远程先创建好分支然后拉取到本地

      - - git checkout -b [本地分支名称] origin/[远程分支名称]

      - 拉取远程分支到本地

      - - git pull origin [远程分支名称]:[本地分支名称]

      - 查看远程仓库

      - - git remote show origin

      - 查看本地分支

      - - git branch

      - 查看远程分支

      - - git branch -r

      - 查看所有分支

      - - git branch -a

      - 删除本地分支

      - - git branch -d [本地分支名称]

      - 删除远程分支

      - - git push origin --delete [远程分支名称]
        - git push origin :[远程分支名称]

      - 设置默认提交分支

      - - git branch --set-upstream-to=origin/[远程分支名称] [本地分支名称]
        - 

  - 工作流       - git work flow

  - GUI工具
