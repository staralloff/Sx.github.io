---
layout: post
title: First Django Pro
category: 技术
tags: Django
keywords: Django
---

## 1. 安装 Django

当前版本是2.0.2，安装虚拟环境，pip安装

```
$ cd dir of django project
$ cd bin
$ source activate
(dir of django project) $ pip3 install django==2.0.2
```

## 2. Test

```
(dir of django project) $ python
Python 3.5.2 (default, Nov 23 2017, 16:37:01)
[GCC 5.4.0 20160609] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import django
>>> django.get_version()
'2.0.2'
>>> 
```

## 3. Run

```
(dir of django project) $ python manage.py runserver
```

![Host](/assets/img/django.png)
