# 基于 Hexo + Next 的个人博客

这是一个使用 [Hexo](https://hexo.io/) 框架和 [Next](https://theme-next.js.org/) 主题搭建的个人博客项目。

## 简介

[Hexo](https://hexo.io/) 是一个快速、简洁且高效的博客框架。它允许你使用 Markdown 编写文章，然后通过简单的命令生成静态网站。本项目利用 Hexo 和 Next 主题，帮助你快速搭建和部署一个功能强大且外观精美的个人博客。

## 快速开始

### 环境准备

在开始之前，请确保你的电脑上已经安装了以下软件：

*   [Node.js](https://nodejs.org/en/)
*   [Git](https://git-scm.com/)

### 安装 Hexo

打开你的终端（例如 Git Bash），然后执行以下命令来全局安装 Hexo 命令行工具：

```bash
npm install hexo-cli -g
```

### 初始化项目

1.  在你想要存放博客的目录下，执行以下命令来初始化一个新的 Hexo 项目：

    ```bash
    hexo init blog
    cd blog
    npm install
    ```

2.  项目初始化完成后，你的 `blog` 文件夹中会包含以下结构：

    *   `node_modules`: 存放项目的依赖包。
    *   `public`: 存放生成的静态网站文件。
    *   `scaffolds`: 存放文章的模板。
    *   `source`: 存放你的文章（Markdown 文件）。
    *   `themes`: 存放博客的主题。

### 本地预览

执行以下命令来启动本地服务器：

```bash
hexo server
```

或者使用缩写：

```bash
hexo s
```

启动成功后，你可以在浏览器中访问 `http://localhost:4000` 来预览你的博客。

## 部署到 GitHub Pages

### 创建 GitHub 仓库

1.  在你的 GitHub 上创建一个新的仓库。仓库的命名规则必须是 `your-username.github.io`。
2.  将 `your-username` 替换为你的 GitHub 用户名。

### 配置 Git

在你的终端中，配置你的 Git 用户名和邮箱：

```bash
git config --global user.name "your-username"
git config --global user.email "your-email@example.com"
```

### 生成和配置 SSH 密钥

1.  执行以下命令来生成一个新的 SSH 密钥：

    ```bash
    ssh-keygen -t rsa -C "your-email@example.com"
    ```

2.  根据提示，找到生成的 `id_rsa.pub` 文件，并将其中的内容复制到你的 GitHub 账户的 SSH and GPG keys 设置中。

### 配置 Hexo 部署

1.  打开项目根目录下的 `_config.yml` 文件。
2.  找到 `deploy` 部分，并修改为以下内容：

    ```yaml
    deploy:
      type: git
      repo: https://github.com/your-username/your-username.github.io.git
      branch: master
    ```

3.  同时，修改 `url` 字段为你的 GitHub Pages 地址：

    ```yaml
    url: https://your-username.github.io
    ```

### 安装部署插件

执行以下命令来安装 Git 部署插件：

```bash
npm install hexo-deployer-git --save
```

### 部署

最后，执行以下命令来生成并部署你的博客：

```bash
hexo clean
hexo generate
hexo deploy
```

或者使用缩写：

```bash
hexo clean
hexo g
hexo d
```

部署成功后，你就可以通过 `https://your-username.github.io` 来访问你的博客了。

## 了解更多

*   [Hexo 官方文档](https://hexo.io/docs/)
*   [Next 主题文档](https://theme-next.js.org/docs/)
