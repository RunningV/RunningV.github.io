---
title: yarn 配置代理镜像
date: 2017-02-08 11:47:41
tags:
---
####	1.yarn 代理设置文档
`https://yarnpkg.com/lang/en/docs/cli/config/`

yarn 官方代理为：
`https://registry.yarnpkg.com`
[国内优秀npm镜像推荐及使用](https://segmentfault.com/a/1190000007657680)
主要以下两个：
	`http://registry.npm.taobao.org/`;
	`http://r.cnpmjs.org/`;
	
#### 2.设置代理地址
`yarn config set registry 'urlxxx'`
#### 3.查看设置：
` yarn config list`
!['配置输出结果'](/images/yarn_config.png)