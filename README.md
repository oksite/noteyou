# NOTEYOU

[中文](README.md) | [English](README_EN.md)

> 开发中早期预览版本（Pre-release）
>
> NOTEYOU 目前由个人开发者维护，功能和数据结构仍可能调整。使用预览版本前，请备份重要文档。

NOTEYOU 是一款基于 Tauri 2、Next.js 和 CodeMirror 6 构建的本地优先 Markdown 桌面编辑器。

无需账号，没有云端同步，也不使用独立笔记数据库。文档以普通的 `.md` 或 `.markdown` 文件保存在本地，用户可以随时使用其他编辑器打开。


## 界面预览

### 暗色主题

![NOTEYOU 暗色主题界面](/dark.jpg)

### 亮色主题

![NOTEYOU 亮色主题界面](/light.jpg)


## 核心特性

### 文件与文件夹管理

- 以树形结构管理文件夹和 Markdown 文档
- 新建、重命名和删除文件或文件夹
- 展开、折叠多级文件夹
- 按名称快速筛选文件树
- 按住同一目录中的文件或文件夹，上下拖动调整顺序
- 自定义顺序持久保存，重新启动后仍然保留
- 在状态栏显示当前实际存储位置

### Markdown 编辑

- CodeMirror 6 编辑器与 Markdown 语法高亮
- 同时打开多个文档标签
- 编辑、分栏、预览三种视图模式
- 支持 GFM、表格、代码块、链接、列表等常用语法
- 标题、加粗、斜体、链接和列表快捷插入工具
- 停止输入 1.2 秒后自动保存
- 支持 `Ctrl/Cmd + S` 手动保存
- 关闭未保存标签前进行确认

### 界面体验

- 中文与英文界面即时切换
- 自动记住上次选择的语言
- 亮色与暗色主题
- 自动记住上次选择的主题
- Windows 原生标题栏主题同步
- 应用内创建、重命名、删除和未保存确认弹窗

## 技术栈

| 层级 | 技术 |
| --- | --- |
| 桌面壳与文件系统 | Tauri 2 / Rust |
| 前端 | Next.js 15 / React 19 / TypeScript |
| 编辑器 | CodeMirror 6 |
| Markdown | marked + DOMPurify |
| 图标 | Lucide React |
| 测试 | Vitest + Testing Library |

Next.js 使用静态导出，前端产物由 Tauri 直接打包进桌面应用。所有本地文件操作都通过 Tauri IPC 交给 Rust 后端执行。

## 下载

> 当前预览版本仅提供 Windows x64 安装包。

[下载 NOTEYOU 最新预发布版](https://github.com/oksite/noteyou/releases)

Windows 用户可以在 Release 页面选择 NSIS `.exe` 安装程序或 `.msi` 安装包。首次启动依赖 Microsoft Edge WebView2 Runtime，现代 Windows 系统通常已经预装。

## 数据存储

NOTEYOU 会优先在可执行文件所在目录创建：

```text
NOTEYOU/DB/
```

如果安装目录不可写，则自动回退到系统应用数据目录。界面底部状态栏会显示当前实际使用的完整路径。

排序信息保存在工作区内的隐藏文件 `.noteyou-order.json` 中，Markdown 文档本身仍然是普通文件。

建议定期备份状态栏显示的整个工作区目录。

## 安全与隐私

- 文件操作集中在 Rust 后端完成
- 只接受工作区内的安全相对路径
- 拒绝绝对路径和 `..` 路径穿越
- 忽略符号链接
- 仅读写 `.md` 和 `.markdown` 文件
- 拒绝 Windows 不支持的文件名字符
- Markdown 预览 HTML 经过 DOMPurify 清理
- 不需要账号，不上传文档，不收集遥测数据

## 当前限制

- 仅提供 Windows x64 预构建版本
- 文件树不会自动监听外部文件变化，需要手动刷新
- 拖拽排序仅限同一目录，不会把文件移动到其他文件夹
- 暂不支持全文搜索和编辑/预览滚动同步
- 窗口大小和位置暂未持久化

## 路线图

- [ ] 文件树监听外部变化并自动刷新
- [ ] 全文搜索
- [ ] 跨文件夹拖拽移动文件
- [ ] 编辑与预览滚动同步
- [ ] 窗口大小和位置持久化
- [ ] macOS 和 Linux 构建

## 本地开发

需要 Node.js、npm、Rust stable、Tauri 对应平台依赖和 WebView2 Runtime。

```powershell
npm install
npm run tauri dev
```

常用命令：

| 命令 | 说明 |
| --- | --- |
| `npm run tauri dev` | 启动完整桌面开发环境 |
| `npm test` | 运行前端测试 |
| `cd src-tauri && cargo test` | 运行 Rust 测试 |
| `npm run build` | 构建 Next.js 静态前端 |
| `npm run tauri build` | 构建桌面程序和安装包 |

仅运行 `npm run dev` 时无法使用依赖 Tauri IPC 的本地文件功能。

## 许可证

本项目采用[木兰宽松许可证，第 2 版](LICENSE)。
