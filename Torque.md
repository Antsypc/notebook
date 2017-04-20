Torque/PBS
======================

## 安装
- Ubuntu 14.04单机安装
- Torque 6.0.3

根据[Admin Guide](http://docs.adaptivecomputing.com/torque/6-0-3/adminGuide/help.htm)逐步下载安装。需要注意的有以下几点：

- 配置系统自启动时，复制`contrib/init.d/`下`debian.`开头的对应文件到`/etc/init.d/`，可以[参考这个](http://blog.sina.com.cn/s/blog_4a0a8b5d0102v2p1.html)
- 执行`./torque.setup root`前，将里面的shell函数写法修改正确。[见此](https://github.com/adaptivecomputing/torque/issues/422)
- 必须修改`/etc/hosts`中对应的主机IP为局域网或公网IP，不能是127开头的保留地址。使用`pbsnodes -a`显示各节点state为free即正常状态。问题描述[见此](https://cmayes.wordpress.com/2012/12/15/single-host-torque-pbs/)



