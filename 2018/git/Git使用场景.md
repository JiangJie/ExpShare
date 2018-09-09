# Git使用场景

## 已有项目提交到GitHub

当我们想要使用GitHub管理我们的项目时，通常的做法是先通过GitHub网站创建空项目，然后在本地clone这个项目，然后往里面加文件再提交。

有时候本地已经是一个git仓库了，如果将本地的文件直接拷贝到从GitHub clone的项目目录下，则本地的提交记录都会丢失，有时候是不能接受的。

保留本地提交记录，同时使用GitHub项目的方法：

1. cd ExpShare
2. git remote add origin https://github.com/JiangJie/ExpShare.git
3. git branch -u origin/master master
4. git pull --allow-unrelated-histories
5. git push

每条命令的说明：

1. 假设本地git项目的根目录叫ExpShare
2. 将通过GitHub创建的项目作为远程仓库添加到本地项目，origin是远程仓库的名字，可以随便取，只是origin用的最普遍；https://github.com/JiangJie/ExpShare.git 是GitHub项目地址
3. 将本地的master分支设置为自动追踪远程仓库的master分支，这里master也只是单纯的分支名，没有特殊含义，只是master用的普遍；-u是--set-upstream-to的缩写，意为本地分支追踪远程分支
4. 增加--allow-unrelated-histories选项是因为本地和远程master没有共同的祖先，无法进行简单的三方合并，必须要显式告诉git做简单的文件合并
5. 一旦将本地和远程master分支建立上追踪关系，就可以将本地的修改提交到远程仓库了