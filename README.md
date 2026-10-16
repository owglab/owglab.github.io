# OWGlab GitHub Pages 维护指南

这是 OWGlab 课题组的公开宣传网页，部署在 GitHub Pages 上。本文档面向所有需要修改网页内容的成员或协作者，说明如何获取代码、修改内容、提交更改并完成部署。

## 网页结构

- `index.html`：主页内容
- `styles.css`：样式表
- `assets/`：图片、SVG 等资源文件
- 页面入口是 `index.html`，首页视觉资产在 `assets/research-system.svg`

推送到 `main` 分支后，GitHub Pages 会自动更新。访问地址通常为 `https://owglab.github.io/` 或管理员绑定的自定义域名。

## 一、获取修改权限

有两种方式可以参与修改：

1. **成为仓库协作者**：联系管理员，将你的 GitHub 账号添加为组织成员或仓库协作者，并授予 `Write` 权限。这样你可以直接向仓库推送分支。
2. **没有写权限？使用 Fork + Pull Request**：任何 GitHub 用户都可以 Fork 本仓库，修改后发起 Pull Request。管理员审核合并后，网页自动更新。

## 二、有写权限时的修改流程

### 第一步：克隆仓库

打开终端，执行：

    git clone https://github.com/owglab/owglab.github.io.git
    cd owglab.github.io

如果实际仓库地址不同，请以管理员提供的为准。

### 第二步：创建新分支

不要直接在 `main` 上修改，创建一个新分支：

    git checkout -b update-homepage

### 第三步：修改文件

用编辑器修改文件：
- 改文字：编辑 `index.html`
- 改样式：编辑 `styles.css`
- 加图片：把图片放入 `assets/`，并在 HTML 中用相对路径引用，例如 `<img src="assets/photo.jpg">`

本地预览：直接用浏览器打开 `index.html`，或使用本地服务器查看效果。

### 第四步：提交更改

修改完成后，保存文件，在终端执行：

    git add .
    git commit -m "描述你的修改，例如：更新导师介绍"

### 第五步：推送到 GitHub 并发起合并

将分支推送到 GitHub：

    git push origin update-homepage

如果远程名不是 `origin`，可以用 `git remote -v` 查看。通常克隆后默认远程名为 `origin`。

然后，在 GitHub 上发起 Pull Request，请求合并到 `main`。等待管理员审核合并。

## 三、无写权限时的修改流程（Fork + PR）

### 第一步：Fork 仓库

打开仓库页面，点击右上角 **Fork**。

### 第二步：克隆你 Fork 后的仓库

    git clone https://github.com/你的用户名/owglab.github.io.git
    cd owglab.github.io

### 第三步：修改并提交

创建分支、修改文件、提交、推送（步骤同上一节第二至第五步）。

### 第四步：发起 Pull Request

在 GitHub 上向原仓库发起 Pull Request：
- base 仓库：`owglab/owglab.github.io`
- base 分支：`main`
- head 分支：你 Fork 中的分支

等待管理员审核合并。

## 四、修改建议与注意事项

- 修改前先拉取最新代码：`git pull origin main`
- 图片等资源请放在 `assets/` 目录，使用相对路径引用
- 不要随意改动 `<head>` 中的元信息，除非你清楚后果
- 保持代码整洁，缩进统一
- 如果只是修改文字，也可以直接在 GitHub 网页上编辑文件并发起 Pull Request
- 部署：合并到 `main` 后，GitHub Pages 通常几分钟内自动更新。可在仓库的 `Actions` 或 `Settings → Pages` 中查看部署状态
