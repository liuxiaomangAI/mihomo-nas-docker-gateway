# Mihomo NAS 全家科学上网方案

这是一个面向中文用户的 Mihomo 部署示例仓库，核心目标是：

- 在 NAS 上通过 Docker 部署 Mihomo
- 将 NAS 作为局域网代理网关
- 让家中设备尽量少折腾地接入代理
- 实现节点订阅与 GEO 数据自动更新

如果你正在找的是“把 Mihomo 部署到飞牛 NAS / 群晖 / 其他 NAS 上，然后让局域网或全家设备统一走代理”，这个仓库就是为这个场景准备的。

## 这个项目是做什么的

简单说，这个项目提供了一套可直接参考的配置和文档，用来实现：

```text
主路由 -> NAS（Docker 中运行 Mihomo）-> 手机 / 电脑 / 平板 / 电视等局域网设备
```

适合下面这些需求：

- 想把代理统一放在 NAS 上，不想每台设备单独折腾
- 想让局域网设备通过网关或 DNS 的方式接入代理
- 想用 Docker 管理，方便迁移、备份和恢复
- 想让订阅节点和 GEO 数据自动更新，减少后续维护

## 仓库包含什么

- [config.yaml](./config.yaml)
  Mihomo 主配置文件
- [docker-compose.yml](./docker-compose.yml)
  用于在 NAS 中通过 Docker Compose 启动 Mihomo
- `GeoSite.dat` / `GeoIP.dat` / `country-lite.mmdb` / `GeoLite2-ASN.mmdb`
  首次启动建议提前放入的 GEO 文件
- [20260330 飞牛NAS部署mihomo实现全家无感翻墙 4个文件自动更新 最终版.md](./20260330%20%E9%A3%9E%E7%89%9BNAS%E9%83%A8%E7%BD%B2mihomo%E5%AE%9E%E7%8E%B0%E5%85%A8%E5%AE%B6%E6%97%A0%E6%84%9F%E7%BF%BB%E5%A2%99%204%E4%B8%AA%E6%96%87%E4%BB%B6%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%20%E6%9C%80%E7%BB%88%E7%89%88.md)
  详细部署文档

## 项目特点

- 面向 NAS 场景，而不是单机客户端场景
- 使用 Docker 部署，结构清晰，迁移方便
- 支持透明代理和 DNS 分流
- 支持订阅自动更新
- 支持 GEO 数据自动更新
- 适合家庭局域网统一接入

## 快速开始

1. 把本仓库文件放到 NAS 上的 Mihomo 配置目录。
2. 准备好你自己的可用订阅链接。
3. 将 [config.yaml](./config.yaml) 中的订阅地址替换为你自己的链接。
4. 确认 4 个 GEO 文件已经在目录中。
5. 使用 [docker-compose.yml](./docker-compose.yml) 在 NAS 中创建并启动容器。
6. 打开 `http://你的NASIP:9090` 检查 Mihomo 控制器是否正常。

## 推荐目录结构

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

## 适合哪些 NAS

这个仓库本质上依赖的是 Docker 和 Mihomo，不强绑定某一个 NAS 品牌。

常见可参考场景：

- 飞牛 NAS
- 群晖 NAS
- 其他支持 Docker / Docker Compose 的 Linux NAS

## 使用前注意

- 不要把真实订阅链接提交到公开仓库。
- 如果配置里包含真实局域网 IP、域名或账号信息，建议先脱敏。
- 首次启动前务必先放入 GEO 文件，否则可能出现启动卡住或在线下载失败。
- `proxy-server-nameserver` 不建议删除，它会直接影响代理节点域名解析稳定性。

## 文档入口

完整部署步骤见：

- [部署说明](./20260330%20%E9%A3%9E%E7%89%9BNAS%E9%83%A8%E7%BD%B2mihomo%E5%AE%9E%E7%8E%B0%E5%85%A8%E5%AE%B6%E6%97%A0%E6%84%9F%E7%BF%BB%E5%A2%99%204%E4%B8%AA%E6%96%87%E4%BB%B6%E8%87%AA%E5%8A%A8%E6%9B%B4%E6%96%B0%20%E6%9C%80%E7%BB%88%E7%89%88.md)

## 一句话总结

这是一个“在 NAS 里通过 Docker 部署 Mihomo，并把 NAS 当作家庭局域网代理网关来使用”的中文项目模板。
