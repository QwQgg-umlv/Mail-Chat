# Mail-Chat 邮聊 📮💬

**像聊天一样用邮箱** —— 微信式的桌面邮箱客户端，邮件收发、AI 助手、日历自动整理，一个不少。

![风格](https://img.shields.io/badge/UI-科技风-00F5A0) ![Python](https://img.shields.io/badge/Python-3.9%2B-blue) ![平台](https://img.shields.io/badge/平台-Windows%20%7C%20macOS-lightgrey)

## ✨ 功能

| 模块 | 说明 |
|---|---|
| 💬 **聊天式收发** | 邮件变成聊天气泡，一人一个会话；双击会话跳到最新未读 |
| 🌍 **自动翻译** | 外语邮件自动翻译成中文，可一键「看原文」（免费翻译引擎 + AI 双保险） |
| 🤖 **AI 助手** | 一键摘要、帮写回复、提取日程（接入任意 OpenAI 兼容 API） |
| 📅 **日历自动整理** | 邮件里提到的时间自动进日历（绿色=确认 / 橙色=待确认），点击可跳回原邮件 |
| 🔍 **Outlook 式搜索** | 全文搜索 + 范围筛选（全部/发件人/主题/正文），关键词高亮、点击直达 |
| 👥 **联系人索引** | 微信同款字母导轨（A-Z 可拖动跳转）+ 星标好友 |
| 🎨 **双色主题** | 科技黑 / 清爽白 随心切换 |
| 📥 **历史邮件导入** | 一键导入全部历史邮件并整理进日历 |
| 🔒 **本地隐私** | 所有数据只存本机（SQLite + JSON），无网页版、无云同步 |

## 🚀 快速开始（Windows）

```bash
# 方式一：直接用打包好的 exe（dist/邮聊.exe）——双击即用

# 方式二：源码运行
python server.py
# 浏览器自动打开 http://127.0.0.1:8765
```

macOS 用户：双击 `1.安装.command` → 再双击 `邮聊.app`。

## 📦 技术栈

- **后端**：Python 标准库（http.server / imaplib / smtplib / sqlite3）—— **零第三方依赖**
- **前端**：原生 HTML / CSS / JS（无框架）
- **邮箱协议**：IMAP IDLE 实时推送 + 轮询降级；SMTP 发信
- **登录**：Microsoft 365 OAuth2（Thunderbird 公共客户端，免注册应用）/ 授权码密码
- **打包**：PyInstaller（单文件 exe）

## 📁 项目结构

```
server.py       # HTTP 服务 + API + OAuth 回调
mail_sync.py    # IMAP 收信（IDLE/轮询）、SMTP 发信、历史导入
oauth_ms.py     # Microsoft OAuth2（登录/换令牌/续期，双路重试）
ai_service.py   # AI 接入（总结/翻译/帮写/提取日程）
timeutil.py     # 中文时间表达解析（"下周三下午3点"）
db.py           # SQLite 存储
static/         # 界面（app.js / tech.css / index.html）
```

## ⚙️ 配置

启动后在「我的」页面配置：
- **邮箱**：预设 Outlook / M365 / Gmail / QQ / 163 一键填服务器
- **AI**：任意 OpenAI 兼容接口（base_url + api_key + model）
- **翻译**：默认免费引擎（仅发送待译句子），可选 AI 翻译

## 📄 License

MIT
