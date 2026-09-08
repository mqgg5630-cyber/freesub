# freesub

自动抓取你配置的订阅源，测活后导出 Clash / V2RayN / sing-box 订阅，并按国家/地区与住宅 IP（家宽）分类。

> 合规提示：请只添加你有权使用的订阅源，遵守当地法律、平台条款与网络服务提供商规则。不要把本项目用于垃圾注册、撞库、爬虫绕风控等滥用场景。


## GitHub Actions 自动更新

当前分支包含 Actions 模板：`docs/workflows/update.yml`。

如果要让 GitHub 自动运行，请在 GitHub 网页端把它复制/新建到 `.github/workflows/update.yml`，并提交到 `arena/01a08039-freesub` 分支；模板带有当前分支的 `push` 触发器，提交后会立即跑一次。Arena 当前 GitHub App 没有 `workflows` 写权限，不能直接推送 `.github/workflows/*` 文件。

## 使用方式

1. 在 GitHub 仓库里进入 **Actions**。
2. 选择 **Update Subscriptions**。
3. 点击 **Run workflow** 手动运行一次；之后会按计划自动更新。
4. 运行成功后，README 会自动写入最新订阅链接：
   - `output/v2ray.txt`
   - `output/clash.yaml`
   - `output/singbox.json`
   - `output/residential.txt`
   - `output/residential-clash.yaml`
   - `output/residential-singbox.json`
   - `output/residential-by-country/` 下的家宽分地区订阅

## 自定义

- 节点名字后缀：手动运行 Action 时填写 `node_name_suffix`；默认使用仓库拥有者名称。
- 订阅源：编辑 `scripts/main.py` 里的 `SOURCE_URLS`；如订阅源带密钥，建议在 GitHub Actions Variables 中设置 `SUB_SOURCE_URLS`（多个 URL 用换行或英文逗号分隔）。本地调试可复制 `sources.txt.example` 为被忽略的 `sources.txt`。
- 更新频率：编辑 `.github/workflows/update.yml` 里的 `cron`。
