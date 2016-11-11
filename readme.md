myblog维护方式：

可实现在不同电脑上写文章维护的功能，原理是在github上创建代码托管仓库，使用`hexo`搭建的博客系统本地文件通过`hexo g -d` 直接发布到代码仓库的`master`,再创建分支`hexo`,将本地的hexo创建的文件`git push`到hexo分支中。master分支托管编译后的静态文件，可在线上访问。hexo分支中是开发文件，在其中修改文章样式等。



后期维护：

1. 在电脑上`git clone` 本项目
2. `npm install`
3. 查看分支一定要在**hexo**分支,修改文件样式。
4. `hexo g -d` 发布到远程master,就可线上访问了
5. `git add && git commit` hexo 分支到远程分支：`git push origin hexo`
6. 每次在不同的电脑要先更新本地文件在修改：`git pull origin hexo`