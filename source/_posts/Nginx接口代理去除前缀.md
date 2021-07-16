---
title: Nginx接口代理去除前缀
date: 2021-07-16 09:58:03
tags:
---

# Nginx配置接口代理去除前缀

前端项目在使用nginx做接口反向代理时，有时候需要根据不同的接口前缀将请求代理到不同的服务器，但是真实的接口请求中又要去掉这个前缀。此时配置主要有两种写法 。

- ######  方法一：在地址后面加/

```
server {
	location ^~/api/ {
		proxy_pass http://127.0.0.1:8080/;
	}
}
```

 `^~/api/`表示请求前缀是`api`的请求，`proxy_pass`最后加上`/`，就会把`api`去除，比 如请求的地址是`api/test`，则代理发出的请求是`http://127.0.0.1:8080/test`

- ###### 方法二：rewrite

  ```
  server {
  	location ^~/api/ {
  		rewrite ^/api/(.*)$ /$1 break;
  		proxy_pass http://127.0.0.1:8080;
  	}
  }
  ```

  使用rewrite重写了url。**注意：proxy_pass后不需要加/**

