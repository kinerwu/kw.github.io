---
title: hexo如何后台线上线下同步？
date: 2017-09-02 14:37:10
tags:
---
在博客目录写一个有关git同步的小脚本:**server-upload.sh** 用来同步VPS目录下的变化，主要代码其实就是先git pull 拉取repo最新, 之后在push. 具体脚本代码不再赘述.

建一个**hexo-deploy**的脚本,内容:

```
hexo g && hexo d
./server-upload.sh
```
利用hexo-admin的deploy功能，可以在线发布，注意修改**_config.yml:** 加上hexo-admin的admin选项, 加一个**deployCommand: ./hexo-deploy**的字段,如下:

```
admin:
    username: XXX
    password: XXXXX
    deployCommand: './hexo-deploy'
```
编辑完博客时候，发布的时候，需要点击hexo-admin的deploy。这样在后台就可以执行前面定义的**hexo-deloy**脚本了

本地机器也需要有一个**upload.sh**的脚本, 每次同样需要先git pull 在git push 到私人repo. 其实就是版本控制那一套.
