# nanobot-lzcapp

懒猫微服版 [nanobot](https://github.com/HKUDS/nanobot) —— 自托管 AI 智能体网关。

- 包名：`cloud.lazycat.app.nanobot`
- 上游：`HKUDS/nanobot` v0.4.0（MIT）
- 镜像：由上游 `Dockerfile` 在 CI 内构建后以 `embed:nanobot` 内嵌进 LPK v2
- 中文：上游自带 `webui/src/i18n/locales/zh-CN` + `zh-TW`
- 免密：`stable_secret` 同时喂给容器 `NANOBOT_WEB_TOKEN` 与浏览器注入脚本

## 构建

`.github/workflows/build.yml` 在 `ubuntu-latest` 上拉上游 tag 的 tarball 到 `upstream/`，
再跑 `lzc-cli project release -o dist`，产物作为 artifact 上传。

上游升级时改 workflow 里的 `UPSTREAM_TAG` 与 `package.yml` 的 `version` 即可。

## 数据目录

`/lzcapp/var/nanobot` → 容器内 `/home/nanobot/.nanobot`（config.json、会话、记忆）。
