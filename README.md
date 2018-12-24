##Git使用  
#视频地址：http://www.56.com/u27/v_MTQ1MDg2NDk2.html  
#视频地址：http://www.56.com/u27/v_MTQ1MDg2NDk2.html  
#1.	git和GitHub？
	git是版权管理工具，GitHub是源代码开发平台，有社交元素，与同行沟通交流  
#2.	git使用
右击打开Git Bash Here，进入C盘根目录，输入以下命令：
$ git config --global user.name "plum"
$ git config --global user.email "your_qq@qq.com”
#用户名可自定义
查看username和useremail命令：
	$ git config –list
	
查看当前目录下的所用文件命令：
	$ ls
进入桌面并创建文件夹名为muyun_crm命令：
	$ cd Desktop/
$ mkdir muyun_crm
进入muyun_crm文件，创建仓库命令：（有.git文件夹）
$ cd muyun_crm/
$ git init
添加文件到仓库命令：
	#将该目录下的所用文件添加到仓库中
		$ git add -A
	#添加一个--文件名	
		$ git add a.txt
#提交—记录修改内容
		$ git commit -m "name commit"
查看修改记录命令：
	$ git log
	简化：$ git log --pretty=oneline

查看文件变动：（如果有就再次添加提交）
	$ git status
#3.	创建GitHub仓库和本地仓库
GitHub仓库：New repository=>创建的仓库名称=>Create repository
#4.	创建ssh钥匙（给予权限）
①点击头像下的settings，进入点击SSH and GPG keys，点击蓝色字体generating SSH keys，进入https://help.github.com/articles/connecting-to-github-with-ssh/界面，点击Generating a new SSH key and adding it to the ssh-agent
，跳转到https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/，
创建钥匙--复制第一行代码：(修改邮箱=如上“your_qq@qq.com”)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
查看钥匙—复制最后一行代码：
ssh-add ~/.ssh/id_rsa
如果查看没有反应，在C盘下搜索.ssh文件夹，然后打开找到id_rsa.pub，打开它，就是所需公钥
②操作如下：（成功会有像气泡的东西）
	a.创建：
Administrator@LM01U25TPBMUSA9 MINGW64 ~
$ ssh-keygen -t rsa -b 4096 -C "your_qq@qq.com"
Generating public/private rsa key pair.

	b.查看：
	$ ssh-add ~/.ssh/id_rsa
	没反应执行以下操作：
		在C盘下搜索.ssh文件夹，然后打开找到id_rsa.pub，打开它，全部复制
c.在GitHub的SSH Keys中点击绿色按钮New  SSH key，输入名称，并将刚复制的代码，粘贴到key下的框框中，点击绿色Add SSH key，即可。
#5.	连接GitHub的仓库
$ git remote add origin https://github.com/xx/xx.git
#6.	将本地仓库移动到GitHub中（提示登录GitHub）
$ git push -u origin master
#7.	下载GitHub仓库的资源到本地
git clone https://github.com/xx/xx.git
>技巧：
1.忘记刚修改的文件是哪个？
git diff  #显示哪个文件，修改了什么
2.版本回退
	获取版本号：$ git reflog
①回退一个版本：$ git reset --hard HEAD^  # ^为回退版本的个数
②回退到指定版本：$ git reset --hard c1ff4cc3  #红色为版本号的前几位
3.分支（团队开发）
	查看分支：$ git branch
	a.创建分支：$ git branch aa #aa为分支名
	b.切换分支：$ git checkout aa  =>(将文件下的东西加入到分支中) $ git add –A  => $ git commit -m "aa commit"
	b.合并分支：进入master  $ git checkout master  =>
$ git merge aa   #aa为分支名
4.网页出现bug时，部分功能可以运行，客户在使用的同时修护bug
在有bug的版本下新建分支，修改bug，完成后，再合并，继续运行
5.删除分支 $ git branch -d aa

6.GitHub fork别人的项目
点击fork，会下载到你的GitHub仓库
7.同步别人的分支
	git clone https://github.com/xx/xx.git
查看源：$ git remote -v
添加别人的源：$ git remote add upstream https://github.com/numbbbbb/Git-Tutorial-By-liaoxuefeng
