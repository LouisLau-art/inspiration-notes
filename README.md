# 💡 灵感收集器 (Inspiration Collector)

> 一个极简的全栈灵感收集工具，旨在提供深夜创作时最纯粹的记录体验。

---

## ✨ 项目亮点

- 🎨 **极简 Apple 风格**：深色模式 (Dark Mode) 优先，莫兰迪柔和暗色系卡片，保护深夜视力。
- 🚀 **单文件架构**：整个前端应用仅包含一个 `index.html`，无需打包、无需构建。
- 🤖 **AI 驱动开发**：由 AI 与开发者协作，在极短时间内完成从逻辑设计到样式优化的全过程。
- 🔗 **全栈功能**：集成了用户注册/登录、数据持久化、实时同步以及数据权限管理。
- 💬 **对话式交互**：底部悬浮对话气泡式输入框，支持回车快捷发送。

## 🛠️ 技术栈

| 组件         | 技术                                                        | 引入方式   | 描述                  |
|:---------- |:--------------------------------------------------------- |:------ |:------------------- |
| **前端框架**   | [Alpine.js](https://alpinejs.dev/)                        | CDN    | 极简响应式逻辑处理           |
| **样式库**    | [Tailwind CSS](https://tailwindcss.com/)                  | CDN    | 原子化 CSS 实现现代感 UI    |
| **后端/数据库** | [PocketBase](https://pocketbase.io/)                      | Binary | 单文件后端 (SQLite + Go) |
| **认证/SDK** | [PocketBase JS SDK](https://github.com/pocketbase/js-sdk) | CDN    | 处理数据交互与登录态          |

## 🚀 快速开始

### 1. 启动后端 (PocketBase)

1. [下载](https://pocketbase.io/docs/) 对应操作系统的 PocketBase 二进制文件。
2. 在终端运行：
   
   ```bash
   ./pocketbase serve
   ```
3. 访问 `http://127.0.0.1:8090/_/` 创建管理员账号。
4. 点击 "New Collection" 创建名为 `notes` 的集合：
   * **字段 (Fields)**:
     * `content` (Type: Text, 必填)
     * `user` (Type: Relation, 关联: users, 必填)
   * **API 权限 (API Rules)**:
     * List/View: `user = @request.auth.id`
     * Create: `user = @request.auth.id`
     * Update: *(留空，禁止修改)*
     * Delete: `user = @request.auth.id`

### 2. 运行前端

由于浏览器安全策略 (CORS)，需要通过本地服务器运行。

**进入项目目录：**

```bash
cd inspiration-collector
```

**使用 Python 启动静态服务器：**

```bash
# Python 3
python3 -m http.server 8000
```

访问 [http://localhost:8000](http://localhost:8000) 即可开始使用。

## 📖 开发心得

### 为什么选择这个技术栈？

为了追求“最简”。我们跳过了复杂的 `npm install` 阶段，通过 CDN 引入依赖。这证明了即使不使用大型框架和复杂的构建流程，依然能做出功能完整、体验丝滑的全栈应用。

### 关于 Python 服务器

`python3 -m http.server` 充当了静态资源服务器。它允许浏览器以 `http` 协议加载页面，从而绕过 `file://` 协议对 AJAX 请求和跨域访问的限制。

## 📂 项目结构

```text
inspiration-collector/
├── index.html       # 唯一的应用代码文件
├── pocketbase       # 后端可执行文件 (已加入 .gitignore)
├── pb_data/         # 数据库存储目录 (已加入 .gitignore)
└── README.md        # 项目文档
```

## 📜 许可证

本项目采用 [MIT License](LICENSE) 开源。

---

**Inspired by Curiosity.** 如果你喜欢这个极简的项目，请给它一个 ⭐！
