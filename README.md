# ego-lite-bing-search

一个用于 **ego lite**（Chromium 156 / Windows）的未打包扩展，把浏览器默认搜索引擎设为 **Bing**（`cn.bing.com`）。

## 功能

- 通过 `chrome_settings_overrides.search_provider` 覆盖默认搜索引擎。
- 地址栏输入任意词回车 → 落到 Bing 搜索结果页（`https://cn.bing.com/search?q=...`，实际会 302 到 `www.bing.com` 并附加 `mkt=zh-CN`）。
- 新标签页搜索框同样走 Bing。
- 纯本地扩展：无后台脚本、无网络请求、不申请权限。

## 安装（未打包）

1. 打开 `chrome://extensions`。
2. 打开右上角「开发者模式」。
3. 点「加载未打包的扩展程序」，选择本目录。
4. 打开 `chrome://settings/search`，应显示 **Bing**，并提示「此设置由“Bing Default Search”控制」。

如果希望浏览器每次启动都自动加载（不必每次手动加载），可在启动命令中加入：

```text
--load-extension=D:/path/to/ego-lite-bing-search
```

Windows 下可把它追加到 ego lite 快捷方式的「目标」参数末尾。

## manifest 要点

- `manifest_version: 3`
- `chrome_settings_overrides.search_provider.is_default` 必须为 `true`（Chromium 156 会校验）
- `search_url` 必须包含 `{searchTerms}`

## 卸载

在 `chrome://extensions` 中移除本扩展；如果用了启动参数，同时删掉 `--load-extension=...` 即可。

## 说明

- 本项目仅为个人使用 / 学习示例，与 Google、微软均无关联；Bing 是其各自所有者的商标。
- 扩展覆盖默认搜索是 Chrome 支持的能力，但如需上架 Chrome Web Store，请先自行确认商店政策。
- 该扩展按「未打包扩展」方式使用，不提供商店安装包。
