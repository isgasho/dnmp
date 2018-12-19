
## 项目结构  
```
docker-lnmp
└── v1.1
    ├── conf                    -- Nginx 配置目录
    │   ├── conf.d
    │   │   └── www.conf        -- Nginx 扩展配置文件
    │   ├── fastcgi.conf
    │   ├── fastcgi_params
    │   ├── mime.types
    │   └── nginx.conf          -- Nginx 主配置文件
    ├── docker-compose.yml      -- Docker Compose 配置文件
    ├── etc                     -- 公共配置目录
    │   ├── letsencrypt         -- Nginx 证书目录
    │   │   ├── ssl.crt
    │   │   └── ssl.key
    │   ├── php-fpm.conf        -- PHP-FPM 进程服务的配置文件
    │   ├── php-fpm.d
    │   │   └── www.conf        -- PHP-FPM 扩展配置文件
    │   └── php.ini             -- PHP 运行核心配置文件
    ├── log                     -- Nginx 日志目录
    │   ├── access.log
    │   └── error.log
    └── www                     -- 项目代码目录
        └── tp5.1               -- 具体项目目录
            ├── application
            │   └── index
            ├── composer.json
            ├── composer.lock
            ├── config
            │   ├── app.php
            └── public
               └──index.php    -- 项目框架入口文件
```
## 项目部署启动
* 项目目录：`docker-lnmp\dev\nginx\v1.1`
* 启动所有容器
    ```
    $ docker-compose up
    Starting lnmp-php7.2.13      ... done
    Recreating lnmp-nginx-alpine ... done
    Attaching to lnmp-php7.2.13, lnmp-nginx-alpine
    ```
* 浏览器输入：`https://127.0.0.1:8088/index/index/hello`
    > 支持Https
* 重启所有容器
    ```
    $ docker-compose restart
    Restarting lnmp-nginx-alpine ... done
    Restarting lnmp-php7.2.13    ... done
    ```
* 停止所有容器
    ```
    $ docker-compose stop
    Stopping lnmp-nginx-alpine ... done
    Stopping lnmp-php7.2.13    ... done
    ```

## HELP
* [Dockerise your PHP application with Nginx and PHP7-FPM](http://geekyplatypus.com/dockerise-your-php-application-with-nginx-and-php7-fpm/)
* [docker-openresty](https://github.com/openresty/docker-openresty)

* *因为相比`nginx:latest`，`nginx:alpine`有几点优势：
    * 用的是最新版nginx镜像，功能与`nginx:latest`一模一样
    * alpine 镜像用的是[Alpine Linux](https://alpinelinux.org/)内核，比ubuntu内核要小很多。
    * `nginx:alpine` 默认支持http2。