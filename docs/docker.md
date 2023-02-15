# Docker 国内源

## 设置

修改 Docker Daemon 配置文件 /etc/docker/daemon.json（不存在则自行创建），添加国内各大厂商提供的镜像加速地址。
以下镜像源按顺序分别为Docker中国、[中科大][1]、网易、百度、腾讯，由于[阿里云镜像加速][2]只面向个人开发者，这里提供文档链接请自行食用。
```json
{
    "registry-mirrors": [
        "http://registry.docker-cn.com",
        "http://docker.mirrors.ustc.edu.cn",
        "https://hub-mirror.c.163.com",
        "https://mirror.baidubce.com",
        "https://mirror.ccs.tencentyun.com"
    ]
}
```

``` bash
# 配置后重启 Docker
$ systemctl daemon-reload
$ systemctl restart docker
```

[1]: https://mirrors.ustc.edu.cn/help/dockerhub.html
[2]: https://help.aliyun.com/document_detail/60750.html

## 查看

``` bash
$ docker info
 <snap>
 Registry Mirrors:
  http://registry.docker-cn.com/
  http://docker.mirrors.ustc.edu.cn/
  https://hub-mirror.c.163.com/
  https://mirror.baidubce.com/
  https://mirror.ccs.tencentyun.com/
 <snap>
```