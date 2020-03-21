---
title: Nginx优化总结（1）
tags:
- Nginx
- Linux
desc: 部署完nginx之后，最重要的则是优化配置。适合的配置，才能发挥服务器最佳的性能。路漫漫其修远兮，吾将上下而求索…
layout: post
---

Curabitur dolor nisi, consectetur id ipsum et, facilisis aliquet est. Aenean nec iaculis nisi. Quisque non nisl eu leo ultrices rhoncus. Pellentesque at euismod est. Pellentesque ac nisi semper, molestie risus vitae, ullamcorper augue. Fusce non eleifend massa, vel mattis urna. Morbi facilisis rutrum eleifend.
<!-- more -->
 Mauris a molestie neque. Aliquam non malesuada nisi, a sodales purus. Nam molestie faucibus sapien eu euismod. Sed scelerisque ornare euismod. In tincidunt est vel pharetra convallis. Praesent vitae nisi odio.

## 修改Nginx配置文件

```shell
vim /opt/nginx/conf/nginx.conf
    user nginx;
    #如果请求数比较多，一般推荐最大修改成CPU内核数等同的值
    worker_processes 1;
    
    events {
        #每个进程可以打开的最大连接数
        worker_connection 1024;
        #可以一次建立多个连接
       multi_accpet on;
       #epoll模式效率更高
       use epoll;
    }
```
