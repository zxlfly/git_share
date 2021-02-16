# git版本控制
版本控制最主要的功能就是追踪文件的变更。
- 工作区(Working Directory)
  - 就是我们能访问的文件系统
- 缓存区(Stage)
  - add之后的位置
- 版本库(Repository)
  - commit之后的位置
- 远程版本库（remote）
  - 集中管理的代码仓库

## 本地版本
创建仓库的过程其实就是将一个普通的文件夹升级成一个具备版本控制功能的文件夹。``git init``实际上git命令在文件夹下创建了一个.git文件夹，版本控制功能的实现，就在这个文件夹内。默认这个文件夹是隐藏不显示的。

### 将文件添加到暂存区
创建一个**bendiwenjia1.js**的文件，随便输入点什么，然后执行``git add bendiwenjia1.js``就可以将其添加到暂存区。一次性添加多个``git add .``

### 查看工作区的状态
``git status``就可以看到变动信息了。

### 从暂存区中恢复文件
一旦提交到版本库，git就会形成快照缓存，如果我们吧文件删掉了，也可以恢复。
``git checkout bendiwenjia1.js``

### 取消跟踪
``git rm --cached bendiwenjia1.js``状态改为未add

### 忽略文件.gitignore
如果你希望在使用 add .的时候忽略某一个文件可以在目录下创建一个 .gitignore文件。  
例如我们要忽略``dist.js``  
创建一个.gitignore的文件输入dist.js即可。

### 提交代码commit
一般是完成某一阶段开发，或者bug修复等情况下，可以创建一次代码提交
``git commit -m 'initapp'``  
将工作区的代码提交到本地仓库中
### 查看工作空间状态
``git status``
### 保存临时工作成果Stash
处于各种原因，可能需要保存现在的工作区的工作情况，去做另一件事，但是又不想提交，就可以用这个功能。
``git stash``报错工作现场到栈中。需要继续之前的工作时使用``git stash pop``，从栈中弹出报错的工作空间现场。但是这种方式可能存在冲突的可能。

### 放弃修改
``git restore .``add和commit都可以撤销至上一次操作的时候，不操作我们的工作区文件

### 回退到上一个提交
git reset 命令用于回退版本，可以指定退回某一次提交的版本。
``git reset [--soft | --mixed | --hard] [HEAD]``-mixed 为默认  
``git reset HEAD^``只是版本回退 不更新工作区  
``git reset --hard HEAD^``不但版本回退 也会更新工作区的文件到上一个版本

## 分支管理
一般在多人协作开发的项目中使用的多，便于管理。
### 创建分支
默认情况下我们处在主分支master。  
- ``git branch (branchname)``创建分支
- ``git checkout (branchname)``切换分支
- ``git checkout -b (branchname)``创建切换分支
- ``git branch -d (branchname)``删除分支
- ``git branch``列出分支``git branch -a``列出分支包括远程的分支
- ``git merge ``分支合并

### 清洗提交历史 -- squash方式合并
可能在做某个功能的时候commit了很多次，不希望这些中间commit被看到，这个时候我们可以用``git status``查看一下发现合并代码后并没有提交。只是将所有的提交都整合到了一起放在暂存区。然后commit。

### 标签管理
给自己的代码打上版本标记。
- ``git tag v1.0``将最新提交打标签
- ``git tag v0.9 4ab034``将指定commit打标签
- ``git tag``查看打标签
- ``git show v0.9``查看与某标签之间的差距

## 远程仓库
- ``git remote -v``查看远程仓库
- ``git remote add [shortname] [url]``shortname 为本地的版本库
- ``git remote rm name``  删除远程仓库
- ``git remote rename old_name new_name``  修改仓库名
- ``git push``推送到远程
- ``git fetch <源>``拉去，之后需要merge合并
- ``git pull``相当与先fetch + merge
  - 例如：把本地的仓库源设置成GitHub的让后推送
  - ``git remote add origin git@github.com:***********``
  - ``git push -u origin master``

### 关于GitHub
- Watch
  - 表示关注、这个项目的所有动态包括PR ISSUE你的信息中心和邮箱都会收到。
- Star
  - 表示点赞、表示对这个项目支持。会添加到star列表方便后续查看
- Fork
  - 相当于复制了目前项目的文件，后续变化必须手动更新。