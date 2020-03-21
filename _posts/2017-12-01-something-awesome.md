---
title: Nginx优化总结（1）
tags:
- Nginx
- Linux
desc: 部署完Nginx之后，最重要的则是优化配置。适合的配置，才能发挥服务器最佳的性能。路漫漫其修远兮，吾将上下而求索…
layout: post
---

对Nginx优化分为两种：Nginx配置文件优化和系统优化

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
