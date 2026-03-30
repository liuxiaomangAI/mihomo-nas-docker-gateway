# mihomo

一个用于在飞牛 NAS 上部署 Mihomo 的示例配置仓库，目标是实现透明代理、DNS 防污染，以及节点和 GEO 数据的自动更新。

## 仓库内容

- [config.yaml](./config.yaml)：Mihomo 主配置
- [docker-compose.yml](./docker-compose.yml)：Docker Compose 启动文件
- `GeoSite.dat` / `GeoIP.dat` / `country-lite.mmdb` / `GeoLite2-ASN.mmdb`：首次启动所需 GEO 文件
- [20260330 飞牛NAS部署mihomo实现全家无感翻墙 4个文件自动更新 最终版.md](./20260330%20%E9%A3%9E%E7%89%9BNAS%E9%83%A8%E7%BD%B2mihomo%E5%AE%9E%E7%8E%B0%E5%85%A8%E5%AE%B6%E6%97%A0%E6%84%9F%E7%BF%BB%E5%A2%99%204%E4%B8%AA%E6%96%87%E4%BB%B6%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%20%E6%9C%80%E7%BB%88%E7%89%88.md)：完整部署说明

## 快速开始

1. 把仓库文件上传到 NAS 上的 Mihomo 配置目录。
2. 将 `config.yaml` 中的订阅链接替换成你自己的可用链接。
3. 确认 4 个 GEO 文件已经在目录内。
4. 使用 `docker-compose.yml` 在飞牛 NAS 中创建并启动项目。
5. 通过 `http://你的NASIP:9090` 检查控制器是否可访问。

## 目录建议

```text
/vol1/1000/Docker/mihomo/
├── config.yaml
├── docker-compose.yml
├── GeoSite.dat
├── GeoIP.dat
├── country-lite.mmdb
├── GeoLite2-ASN.mmdb
├── providers/
└── backup/
```

## 使用前注意

- 不要把真实订阅链接直接提交到公开仓库。
- 如果有局域网真实 IP、域名、账号信息，也建议先脱敏。
- 首次启动前务必先放入 GEO 文件，否则容易出现启动卡死或在线下载失败。
- `proxy-server-nameserver` 建议保留，它直接影响代理节点域名解析稳定性。

## 文档入口

完整部署步骤见：

- [部署说明](./20260330%20%E9%A3%9E%E7%89%9BNAS%E9%83%A8%E7%BD%B2mihomo%E5%AE%9E%E7%8E%B0%E5%85%A8%E5%AE%B6%E6%97%A0%E6%84%9F%E7%BF%BB%E5%A2%99%204%E4%B8%AA%E6%96%87%E4%BB%B6%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%20%E6%9C%80%E7%BB%88%E7%89%88.md)
