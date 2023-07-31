---
layout: post
title:  "ssh gitpod 实现科学上网"
tags: hack
---

gitpod.io提供了在线Vscode编辑环境，并且允许ssh登录到你的在线工程。 `ssh user@example.com -D 1080` 实现了端口转发，相当于开启了一个本地Sock5代理。浏览器插件SwitchyOmega可以设置sock5代理127.0.0.1:1080上网。这样，你就可以利用gitpod的云端服务器做中转实现科学上网。亲测连接YouTube，Google，Netflix，tiktok没问题，而且速度非常快。

具体步骤如下:
1. 浏览器(Edge, Chrome, Firefox)中打开 https://gitpod.io/#https://github.com/gitpod-io/template-x11-vnc 使用github账号登录gitpod，等待出现网页内的vscode界面
2. 访问 https://gitpod.io/workspaces ，展开绿点工程行末的三点按钮，点击 Connect Via SSH
3. PowerShell 中 `ssh 'gitpodsampl-templatex11-3qb0#-7...6b.ssh.ws-us102.gitpod.io' -D 1080`, 也就是按第二步中的提示后面还加上 `-D 1080` 实现端口转发，开启sock5代理 127.0.0.1:1080
4. 另一浏览器中安装witchyOmega扩展，设置sock5代理127.0.0.1:1080上网，访问 youtube.com !!!

注：
1. gitpod.io免费版有使用时间限制 50小时/月。
2. 打开的gitpod工程vscode界面中如果几十分钟不操作，可能自动关闭。
相信这两个都不是问题，你有好的办法对付！
