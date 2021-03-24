# 部署学习笔记

* [linux入门指南](https://www.runoob.com/linux/linux-file-attr-permission.html)
* 指令
  * [Linux需要掌握的一些命令](https://www.runoob.com/w3cnote/linux-useful-command.html)
  * [linux命令详解 make/configure/make install](https://www.cnblogs.com/tinywan/p/7230039.html)
  * [systemd介绍](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)
* 最佳实践
  * [阿里云](https://help.aliyun.com/document_detail/50775.html?spm=a2c4g.11186623.6.1259.12a4500dv8Z7Wf)
  * [腾讯云](https://cloud.tencent.com/document/product/213/38237)
* 虚拟机配置
  * [unable to resolve host address的解决方法](https://www.shuzhiduo.com/A/MAzAkDo59p/)
  * [不能访问到虚拟机的web服务器](https://www.shuzhiduo.com/A/MAzAkDo59p/)
* 部署
  * 手动部署:rar压缩-xshell（lrzsz）推送->rar解压
    * nginx安装
    * xshell+lrzsz推送到服务器
    * rar解压：usr/share/nginx/html
    * 修改nginx.conf文件：location/root为usr/share/nginx/html
    * 重载配置：nginx -s reload
  * 自动部署1：[Jenkins + Git + Nginx 一键部署前端静态站点](https://juejin.cn/post/6844903886352809991)
  * 自动部署2：[瓦力部署](https://www.jianshu.com/p/57d47e8f3b97)
* FAQ
  * [centos7 yum安装"No package nginx available."问题](https://blog.csdn.net/boolbo/article/details/72580104)
* 技巧
  * 虚拟机复制：Ctrl+Alt然后再Ctrl+V
