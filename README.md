# git版本控制
版本控制最主要的功能就是追踪文件的变更。

## 本地版本
创建仓库的过程其实就是将一个普通的文件夹升级成一个具备版本控制功能的文件夹。``git init``实际上git命令在文件夹下创建了一个.git文件夹，版本控制功能的实现，就在这个文件夹内。默认这个文件夹是隐藏不显示的。

### 将文件添加到版本库
创建一个**bendiwenjia1.js**的文件，随便输入点什么，然后执行``git add bendiwenjia1.js``就可以将其添加到版本库。一次性添加多个``git add .``

### 查看版本库的状态
``git status``就可以看到变动信息了。

### 从暂存中恢复文件
一旦提交到版本库，git就会形成快照缓存，如果我们吧文件删掉了，也可以恢复。
``git checkout bendiwenjia1.js``

### 取消跟踪
``git rm --cached bendiwenjia1.js``


### 忽略文件.gitignore
如果你希望在使用 add .的时候忽略某一个文件可以在目录下创建一个 .gitignore文件。  
例如我们要忽略``dist.js``  
创建一个.gitignore的文件输入dist.js即可。