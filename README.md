# NOTEYOU

> 🚧 开发中早期预览版本（Pre-release）
> 本项目目前由个人开发者维护，功能仍在快速迭代，
> 不保证数据兼容性，请不要在存放重要笔记的目录中直接使用。

NOTEYOU 是一款基于 Tauri 2 + Next.js + CodeMirror 6 的
本地优先 Markdown 桌面编辑器。无账号、无云端、无独立数据库，
所有文档以普通 `.md` 文件保存在本地应用数据目录中。

## ✨ 核心特性

- 本地文件夹树形管理 Markdown 文件
- CodeMirror 6 编辑 + 语法高亮
- 多标签、编辑/分栏/预览三视图
- 停止输入 1.2 秒自动保存，`Ctrl/Cmd + S` 手动保存
- GFM、表格、代码块、亮/暗主题
- Windows 原生标题栏主题同步

## 🛠 技术栈

| 层级 | 技术 |
| --- | --- |
| 桌面壳 | Tauri 2 / Rust |
| 前端 | Next.js 15 / React 19 / TypeScript |
| 编辑器 | CodeMirror 6 |
| Markdown | marked + DOMPurify |

## 📦 下载

> ⚠️ 当前为开发预览版，仅提供 Windows x64 安装包

- [NOTEYOU 最新预发布版](https://github.com/oksite/noteyou/releases)

## 🗺 路线图

- [ ] 窗口大小/位置持久化
- [ ] 文件树监听外部变化自动刷新
- [ ] 全文搜索
- [ ] 拖拽移动文件
- [ ] macOS / Linux 构建

## ⚖️ 安全与隐私

所有文件操作在 Rust 后端完成，仅允许 `db/` 下的相对路径，
拒绝 `..` 路径穿越与非法文件名，仅读写 `.md` / `.markdown`。
本软件不收集任何遥测数据。

## 📄 License

MIT
