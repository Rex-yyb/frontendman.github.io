# CenterOS 常用指令


## 文件和目录

**目录说明**

* `/`：根目录，绝对目录
* `~`：用户目录，如root用户的目录就是`/root/`
* `..`：上一级目录，相对目录
* `.`：当前目录

**文件属性**

![](./images/file-prop.jpg)

**常用指令**

| 指令                         | 说明                                                                      |
| ---------------------------- | ------------------------------------------------------------------------- |
| **切换目录**                 | **cd(change directory)**                                                  |
| `cd ~`                       | 返回用户目录，如`/root/`                                                  |
| `cd ..`                      | 返回上一级目录                                                            |
| `cd ../..`                   | 向上跳两级目录                                                            |
| `cd /etc/conf`               | 切换到根目录下`/etc/conf`目录                                             |
| `cd etc/conf`                | 切换到当前目录下的`etc/conf`子目录                                        |
| `cd -`                       | 返回上次所在目录                                                          |
| **显示当前目录**             | **pwd(print work directory)**                                             |
| `pwd`                        | 显示当前目录                                                              |
| **查看目录和文件信息**       | **ls(list files)**                                                        |
| `ls`                         | 列出当前目录下所有内容                                                    |
| `ls -a`                      | 列出全部文件，包含`.`开头的                                               |
| `ls -l`                      | 列出文件和目录详情（创建时间、类型、权限情况）                            |
| `ls -rtl`                    | 按时间倒序显示详情                                                        |
| `ls -rtl etc`                | 查看`etc`目录下的文件和目录详情                                           |
| `ls -RF`                     | 列出当前目录和所有子目录情况                                              |
| **创建目录**                 | **mkdir(make directory)**                                                 |
| `mkdir dir1`                 | 创建目录`dir1`                                                            |
| `mkdir dir1  dir1`           | 创建目录`dir1` 、`dir2`                                                   |
| `mkdir -p dir1/dir2`         | 创建多层目录`dir1/dir2`                                                   |
| **删除空目录**               | **rmdir(remove directory)**                                               |
| `rmdir dir1`                 | 删除空目录`dir1`                                                          |
| `rmdir -p dir1/dir2`         | 删除多级空目录`dir1/dir2`                                                 |
| **删除文件或目录**           | **rm(remove)**                                                            |
| `rm -f  file1`               | 强制删除文件                                                              |
| `rm -rf  dir1`               | 强制删除dir1目录                                                          |
| **移动（重命名）文件或目录** | **mv(move)**                                                              |
| `mv file1 file2`             | 重命名`file1`为`file2`                                                    |
| `mv file1 dir1`              | 移动文件`file1`到`dir1`                                                   |
| `mv file1 dir1/file2`        | 移动文件`file1`并重命名为`file2`                                          |
| `mv dir1/* dir2`             | 将dir1下所有文件，移动到dir2                                              |
| `mv dir1 dir2`               | `dir2`存在：移动到`dir2`下<br/>`dir2`不存在：移动并重命名为`dir2`         |
| **复制文件或目录**           | **cp(copy)**                                                              |
| `cp -r dir1 dir2`            | `dir2`存在：复制`dir1`到`dir2`下 <br/> `dir2`不存在：复制并重命名为`dir2` |
| `cp file1 file2`             | 复制文件为`file2`                                                         |
| `\cp -r dir1 dir2`           | 复制并覆盖重名文件                                                        |
| `cp -r dir1/* dir2`          | 复制`dir1`下所有文件到`dir2`                                              |
| `cp -r dir1/* .`             | 复制`dir1`下所有文件到`.`当前目录                                         |
| **创建文件**                 |                                                                           |
| `touch test1.js`             | 创建文件`test.js`                                                         |
| **查看文件内容**             |                                                                           |
| `cat file`                   | 由第一行开始显示文件内容                                                  |
| `cat -n file`                | 由第一行开始显示文件内容，显示行号                                        |
| `tac  file`                  | 倒序显示文件内容（最后一行排最前面）                                      |
| `head -2 file`               | 显示前2行                                                                 |
| `tail -2 file`               | 显示最后3行                                                               |
| `less file`                  | 一页一页翻页查看文件，`pagedown`向下翻页,`pageup`向上翻页，`q`退出        |
| **文件查找**                 |                                                                           |
| `whereis nginx`              | 显示`nginx`文件或目录位置                                                 |
| `find . -name *.js`          | 查找当前目录及子目录下，所有后缀为`.js`的文件，文件名称支持正在匹配       |
| `find . -user root`          | 查找当前目录及子目录下，所有者是`root`的文件和目录                        |
| `find . -type f`             | 查找当前目录及子目录下的一般文件，`d`目录，`f`一般文件                    |
| `find / -ctime -20`          | 根目录及子目录下查找，最近20天创建的文件                                  |
| `find / -type -f -mtime -10` | 根目录及子目录下查找，最近10天内更新过的一般文件                          |
| **文件内容查找**             |                                                                           |
| `grep str file`              | 在文件`file`中，查找字符串`str`                                           |
| `grep str dir/*`             | 在目录`dir`下，查找字符串`str`                                            |
| `grep str -r dir`            | 在目录`dir`以及子目录下，查找字符串`str`                                  |


## 权限

![](./images/file-permission.png)

* `r` 代表可读(read)
* `w` 代表可写(write)
* `x` 代表可执行(execute)
* `-` 代表没有该权限

通过`u`, `g`, `o` 来代表三种身份的权限
* `u`:`user`,用户，所有者
* `g`:`group`，用户组
* `o`:`other`，其他人

除了字母外，还可以用数字来代表权限，例如`rwxr-xr-x`=`(4+2+1)(4+0+1)(4+0+1)`=`755`
* `r`:`4`
* `w`:`2`
* `x`:`1`

| 指令                   | 说明                                           |
| ---------------------- | ---------------------------------------------- |
| **chmod(change mode)** | **更改用户权限**                               |
| `chmod u=rwx,g=rw,o=r` | 赋予所有者`rwx`权限，当前用户组`rw`，其他人`r` |
| `chmod 777`            | 赋予所有人`rwx`权限                            |

## nginx

| 指令              | 说明         |
| ----------------- | ------------ |
| `nginx -t`        | 查看状态     |
| `nginx -s reload` | 重新载入配置 |
| `nginx -s reopen` | 重启         |
| `nginx -s stop`   | 停止         |

## systemctl

**Unit管理**
       
| 指令                          | 说明           |
| ----------------------------- | -------------- |
| `systemctl restart <service>` | 重启服务       |
| `systemctl stop <service>`    | 停止服务       |
| `systemctl start <service>`   | 启动服务       |
| `systemctl kill <service>`    | 杀死服务       |
| `systemctl reload <service>`  | 重载服务的配置 |

* 参考资料
  * [Systemd 入门教程：命令篇](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)

## yum包管理器

| 指令                       | 说明                  |
| -------------------------- | --------------------- |
| `yum install <package>`    | 安装rpm包（需要确认） |
| `yum -y install <package>` | 自动安装rpm包         |
| `yum update  <package>`    | 安装包                |
| `yum -y update`            | 更新系统中所有rpm包   |
| `yum remove <package>`     | 更新系统中所有rpm包   |
| `yum list`                 | 查看安装的rpm包       |
| `yum clean all`            | 清除缓存              |
| `yum search <package>`     | 在rpm仓库中查找       |

## tar文件打包

`.tar.gz`|`.tgz`：一般情况下是源代码的安装包，将源文件以`tar`方式打包后进行`gzip`压缩

| 指令                                | 说明                                            |
| ----------------------------------- | ----------------------------------------------- |
| `tar -czvf dist.tar.gz file1 file2` | 将文件`file1``file1`打包压缩到`dist.tar.gz`文件 |
| `tar -czvf dist.tar.gz *`           | 压缩当前目录下所有文件到`dist.tar.gz`文件       |
| `tar -xzvf dist.tar.gz`             | 解压`dist.tar.gz`到当前目录                     |
| `tar -tf dist.tar.gz`               | 查看`dist.tar.gz`文件内容                       |

* 参考资料
  * [tar指令详解](https://blog.csdn.net/freeking101/article/details/51480295)

## 网络

| 指令         | 说明           |
| ------------ | -------------- |
| `ip address` | 显示当前ip信息 |
| `netstat`    | //TODO         |

## 系统

| 指令              | 说明         |
| ----------------- | ------------ |
| `shutdown -r now` | 重启         |
| `reboot`          | 重启         |
| `shutdown -h now` | 立即关机     |
| `shutdown -h +10` | 十分钟后关机 |

## vim

| 指令     | 说明                        |
| -------- | --------------------------- |
| 普通模式 | 运行`vim file` 打开查看文件 |
| 插入模式 | 按`i`进入，开始编辑文件     |
| 替换模式 | 按`R`进入                   |
| 可视模式 | 按`v`进入                   |
| 命令模式 | 按`:`进入                   |

**编辑文件的过程**

* Step1：按`i`进入插入模式，开始编辑
* Step2：按`ESC`退出插入模式
* Step3：按`:`进入命令模式
* Step4.1：按`q!`不保存并退出
* Step4.2：按`wq`保存并退出