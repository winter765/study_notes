##ubuntu下搭建ROR开发环境

### 安装rvm(ruby版本管理)
	1. 首先要安装curl
	    dpkg -s curl(检查当前是否已安装)
		sudo apt-get install curl(安装curl)
    2. 用rvm官方推荐的方法安装curl -L get.rvm.io | bash -s stable
	    根据完成后的提示，需要运行source ~/.rvm/sripts/rvm
		另：修改~/.bash_profile文件，加入：
		[[ -s "$HOME/.rvm/scripts/rvm" ]] && . "$HOME/.rvm/scripts/rvm" # This loads RVM into a shell session.
        这是网上的方法，但是在我的电脑上每次重新打开终端时都必须要重新输入一遍source ~/.rvm/scripts/rvm，最后我把这句话加在了~/.bashrc文件的最后面，终于解决这个问题了
    3. 使用rvm安装ruby
	    rvm install 1.8.7
		rvm install 1.9.3
		这是我目前安装的版本
	4. 安装rails
	    这里要将ruby版本和rails的不同版本绑定，需要起个名字：
		rvm --create use 1.9.3@rails3.2.6
		这里的1.9.3@rails3.2.6就是要使用的名称，可以根据需求的rails版本更换，是用rvm use [名称]更换不同的版本就成
    5. 安装完成，测试安装成果：
	    ruby -v
		rails -v
