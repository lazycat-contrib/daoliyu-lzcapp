# daoliyu-lzcapp

道理鱼音乐管理系统的懒猫微服 LPK v2 配置。

## 运行配置

- 上游镜像：`msmkls/daoliyu-music:0.3.5`
- 运行镜像：`docker.1ms.run/msmkls/daoliyu-music:0.3.5`
- Web 端口：`4000`
- 多实例：每位懒猫用户运行独立实例
- 音乐目录：默认将用户目录下的 `music` 挂载到 `/app/runtime/library`
- 数据目录：`/lzcapp/var/data`
- 转码缓存：`/lzcapp/var/cache/transcoding`

源 Compose 中可选的 `/dev/snd` 声卡直通未加入商店包，避免多实例默认占用宿主声卡。

## 构建

```bash
lzc-cli project release -o dist/daoliyu.lpk
```

## 自动发布

GitHub Actions 仅启用喵喵商店发布，不启用官方应用商店。仓库需要可用的 GitHub Secrets：

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `PRIVATE_STORE_GROUP_CODES`（可选）

镜像更新由 `ca-x/lazycat-github-action@v1` 检查，并通过 `docker.1ms.run` 镜像模板交付。
