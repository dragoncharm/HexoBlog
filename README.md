hexo + next 框架下的个人博客


详情参见 知乎文章(!https://zhuanlan.zhihu.com/p/618864711)

hexo创建个人博客
hexo是什么？

正如hexo的首页所显示的，它是一款非常快速，简介，高效的博客框架平台，我们可以利用hexo快速生成博客网站的模板，然后部署为我们自己的博客网站。




直接进入操作：

在任意盘符中新建 hexo 文件夹，这里我创建在了F盘



打开hexo文件夹，空白的地方右键，选择 Git Bash Here ，即我们使用 git 环境创建 hexo的blog模板（必须提前安装好 git），打开后如下图所示：/ f / hexo表示当前操作位置在 F盘的 hexo文件夹中




在 git窗口中依次输入以下命令
npm install hexo-cli -g
hexo init blog
cd blog
npm install
hexo server
全部输入完成后，hexo文件夹中便会生成一个 blog 子文件夹，并且blog文件夹里面包含有很多信息：



关于这些文件夹，做一个简单的介绍：

node_modules: 依赖包
public：存放生成的页面
scaffolds：生成文章的一些模板
source：用来存放你的文章
themes：主题
然后输入这两条命令：

hexo g
hexo s
完成后会显示如下内容，则说明配置成功!




在 git 中输入 Ctrl+C 即可关闭hexo s的内容。

打开浏览器，在浏览器输入 localhost:4000 即可进入你的初始默认博客

它长这样：



注意：这只是一个离线版本的博客 ，只能你自己看见，因此我们还需要 GitHub或者 gittee提供的 ssh功能将他变为对外开放的。

GitHub创建仓库
首先注册一个GitHub的仓库，然后在个人主页中选择 new 新建仓库
注意： 仓库名称的前半部分与你的用户名一致，即 lummod，后半部分 为 .http://git.io 固定格式（忽略红色警告，因为我已经创建过了！），可以选择一个readme为说明文件（随便），然后点击创建仓库



回到 git bash黑窗口中，输入以下两个命令（逐条）：
yourname改为你的GitHub的用户名

git config --global user.name "yourname"
youremail改为你的注册GitHub时的邮箱

git config --global user.email "youremail"
一定不要输入错，这样github才能检查到这个用户属于你

创建 ssh，输入命令，然后一直回车
youremail改为你的注册GitHub时的邮箱

ssh-keygen -t rsa -C "youremail"
之后会提示你已完成 ssh的创建，在文件中找到这个路径




记住这两个文件

在 GitHub的 Setting里面，找到 SSH keys，把 id_rsa.pub 里面的内容全部复制到 key 进去，title随便写一个就行



操作完成后，就成功了。

hexo部署到GitHub
在 blog文件夹下面找到 _config.yml 文件，这是属于 你的博客的配置文件，点进入一看就知道了，你可以在这里面直接修改 姓名，内容，等用户的信息。双击打开它（vscode或者其他文本编辑器，记事本都可以）





先找一下有没有以下这段内容（我也忘记了是我添加的还是自带的），如果自带则一定是空的，则修改为如下所示，如果没有，则直接复制下面内容到 文档的末尾：
user表示你的GitHub的用户名

# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
# deploy:
#   type: ''
deploy:
  type: git
  repo: https://github.com/username/username.github.io.git
  branch: master
  # message: Site updated: {{ now('YYYY-MM-DD HH:mm:ss') }})
说明：类型是 git，远程 ssh连接是 你的 repo输入项，branch 输入gh-pages。

另外，找到 第16行（或者直接搜索 url）修改url 为

https://username.github.io
同样username是你的GitHub的用户名。

完成后，保存文件并且退出，在 git bash中输入以下命令：
表示安装 git部署命令工具

npm install hexo-deployer-git --save
最后输入以下三行命令：
hexo clean
hexo g
hexo d
其中 hexo clean清除了你之前生成的东西，也可以不加。 hexo generate 顾名思义，生成静态文章，可以用 hexo g缩写 hexo deploy 部署文章，可以用hexo d缩写

如果是在离线端即 localhost:4000端测试你的博客，则只需要 hexo g + hexo s 即可，无需 hexo d

输入完成后会出现一堆内容，不用管他，只要最后内容如下所示，就表示成功了！




然后你就可以在

username.github.io  # https://username.github.io
访问到你的博客了，其中username是你GitHub用户名，这个网站不是离线的，其他人都可以访问到！！！