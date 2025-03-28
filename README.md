# 一键 Docker 部署 XrayR

### 先决条件

1. vps Ubuntu 20.04 1 台
2. 做好域名解析
3. 开放端口：`80` 必须，（其他端口根据需要自行开放）
4. 修改 `config.yml` 配置文件。[点击下载](https://github.com/Skyler-May/Docker-XrayR/blob/main/config.yml)
5. 修改 `docker-compose` 配置文件。[点击下载](https://github.com/Skyler-May/Docker-XrayR/blob/main/docker-compose.yml)
6. 将 `config.yml` 与 `docker-compose.yml` 上传到 `root` 目录下

### 务必在 `root` 目录下执行一键安装

```bash
wget https://raw.githubusercontent.com/Skyler-May/Docker-XrayR/refs/heads/main/install_XrayR.sh \
     https://raw.githubusercontent.com/Skyler-May/Docker-XrayR/refs/heads/main/update_XrayR.sh \
  && chmod +x install_XrayR.sh update_XrayR.sh \
  && ./install_XrayR.sh
```

## 附加：

### 查看日志需要手动进入 `XrayR` 目录

```bash
cd XrayR-release
docker-compose logs
```

### 更新 XrayR 直接在 root 目录下执行：`./update.sh` 或执行以下：

> 删除容器并重启，更新软件后 config.yml 不会被更新覆盖。
>
> 注意在 docker-compose.yml 所在的目录下执行：

```bash
cd XrayR-release
docker-compose pull
docker-compose up -d
```

### 开启 Ubuntu 系统自带的 BBR 加速

```bash
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
lsmod | grep bbr
```

## [官方文档](https://xrayr-project.github.io/XrayR-doc/xrayr-xia-zai-he-an-zhuang/install/docker.html)
