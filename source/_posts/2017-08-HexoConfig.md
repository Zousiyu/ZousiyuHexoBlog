---
title: HexoConfig
date: 2017-08-18 21:18:10
categories:
- Geek
tags:
- web
- Node.js
---
zousiyu的hexo配置
<!-- more -->

# 标签和分类页面的添加
定位到站点根目录，使用`hexo new page`新建一个**页面**（不是文章）并命名为**tags**，source目录下会出现一个新的文件夹——**tags**。
```
$ hexo new page tags
```

编辑`source\tags\index.md`，添加`type: "tags"`，这意味着这个页面将作为标签云页面。（可选关闭评论）
```markdown
---
title: tags
date: 2017-08-18 21:24:28
type: "tags"
comments: false
---
```

修改主题配置文件，添加**tags**，以使**标签**菜单能正确链接。
```
menu:
  tags: /tags
```

分类同理。

# 部署
由于穷也没有信仰，所以部署到GitHub。修改站点配置文件的部署选项为：
```
deploy:
  type: git
  repo: <repository url>
  branch: [branch]
  message: [message]
```
然后安装`hexo-deployer-git`插件。现在可以部署到GitHub个人页面了。
```
npm install hexo-deployer-git --save
```
**如果遇到秘钥问题，直接上github帮助页面[Connecting to GitHub with SSH - User Documentation](https://help.github.com/articles/connecting-to-github-with-ssh/)，不要瞎几把搜中文教程，都是半吊子。**