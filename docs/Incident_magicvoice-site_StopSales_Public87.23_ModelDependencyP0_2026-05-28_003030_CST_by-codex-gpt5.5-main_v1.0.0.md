# Incident · magicvoice-site Stop Sales · Public 87.23 Model Dependency P0

作者 / AI 来源：Codex GPT-5.5 主脑  
模型或执行端：gpt-5.5-codex  
版本号：v1.0.0  
日期时间：2026-05-28 00:30:30 周四 北京时间 (CST)  
状态：STOP_SALES_SITE_PATCH / PUBLIC_87_23_NO_GO / R2_DMG_NOT_MODIFIED

## 1. 触发原因

Codex Round 1 + Round 2 红蓝军与 Claude v1.0.7 cross-AI review 均确认：官网 Build87.23 public release DMG 约 10MB，未内置 ASR 模型；Harry 本机能识别依赖已有 `~/.config/magicvoice/models` 缓存，不代表新用户首次安装可用。

## 2. 本站止血动作

本次只改 `magicvoice-site` 静态页面：

1. 新增 `/release-update.html` 临时说明页。
2. 首页顶部新增状态条：安装包正在更新，下载与购买暂时暂停。
3. 所有站内直接 DMG 下载链接从 `downloads.ariamagicvoice.com/AriaMagicVoice_2.2.0.dmg?v=87.23-142217` 改到 `/release-update.html`。
4. Paddle checkout 入口改为跳转 `/release-update.html`，不再打开付款弹窗。

## 3. 没做什么

- 未修改 Cloudflare R2 中的 DMG 对象。
- 未上传 87.24。
- 未打包 App。
- 未修改 Paddle 后台产品或价格。
- 未删除历史 87.23 文件。

## 4. 验证

本地静态扫描：

```text
rg "downloads\\.ariamagicvoice\\.com|AriaMagicVoice_2\\.2\\.0\\.dmg|Paddle\\.Checkout\\.open" .
```

应无命中，表示站内直接下载和 checkout open 已阻断。

## 5. 下一步

继续推进 `87.24` bundled minimal ASR model hotfix。恢复下载和购买前必须通过 clean-machine first install gate。

## 6. 检索钩子

`MAGICVOICE_SITE_STOP_SALES_PUBLIC87_23_MODEL_P0` / `RELEASE_UPDATE_PAGE_ACTIVE` / `PADDLE_CHECKOUT_DISABLED_SITE_PATCH` / `R2_DMG_NOT_MODIFIED` / `87_24_REQUIRED_BEFORE_RESUME_SALES`
