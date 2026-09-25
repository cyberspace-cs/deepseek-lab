# 🐋 DeepSeek Lab

> 深度求索（DeepSeek）产品、Harness 框架、生态工具一站式学习仓库
> 
> 持续更新中...

---

## 📖 目录

- [什么是 DeepSeek？](#-什么是-deepseek)
- [DeepSeek 产品矩阵](#-deepseek-产品矩阵)
- [DeepSeek Harness 详解](#-deepseek-harness-详解)
- [快速开始](#-快速开始)
- [新手入门教程](#-新手入门教程)
- [核心示例](#-核心示例)
- [下载地址](#-下载地址)

---

## 🐋 什么是 DeepSeek？

**DeepSeek（深度求索）** 是中国最顶尖的大模型公司之一，由梁文锋创立。

| 项目 | 说明 |
|------|------|
| **总部** | 杭州 |
| **成立时间** | 2023 年 |
| **代表模型** | DeepSeek-V3、DeepSeek-R1、DeepSeek-Coder |
| **开源策略** | 核心模型全部开源，MIT 协议 |
| **定位** | AGI 通用人工智能，从模型到基础设施全栈自研 |

### 核心成就

- 🚀 DeepSeek-R1：推理能力对标 OpenAI o1，完全开源
- 💰 训练成本极低：V3 训练仅用 557 万美元，震惊业界
- 🌍 全球开源社区最活跃的中国大模型
- 🏢 客户：字节跳动、腾讯、阿里、美团等大厂

---

## 📦 DeepSeek 产品矩阵

```
DeepSeek 生态
├── 🧠 大模型
│   ├── DeepSeek-V3（通用对话）
│   ├── DeepSeek-R1（推理增强）
│   ├── DeepSeek-Coder（代码专用）
│   └── DeepSeek-OCR（图像文字识别）
│
├── 🛠️ 开发者工具
│   ├── DeepSeek API（官方接口）
│   ├── DeepSeek Harness（Agent 运行时）⭐
│   └── DSec（沙箱基础设施）
│
├── 💬 应用产品
│   ├── DeepSeek 网页版
│   ├── DeepSeek 桌面版（内测中）
│   └── DeepSeek 移动端 App
│
└── 🏗️ 基础设施
    ├── 3FS 分布式文件系统
    └── DSec Agent 训练沙箱
```

---

## 🚀 DeepSeek Harness 详解

### 什么是 Harness？

**DeepSeek Harness（简称 dsh）** 是 DeepSeek 开源的 **Agent 运行时框架**，核心理念是：

> **一切皆插件（Everything is a Plugin）**

模型、工具、技能、会话、沙箱、存储、Agent 循环、调度、UI —— 全部是可插拔的模块，可以自由替换和组合。

### 架构图

```
┌─────────────────────────────────────┐
│           用户界面（UI）              │
│   桌面版 / Web UI / CLI / 移动端     │
├─────────────────────────────────────┤
│         Agent 循环（Loop）           │
│   思考 → 调工具 → 观察 → 再思考      │
├─────────────────────────────────────┤
│         插件层（Plugins）            │
│  ┌──────┐ ┌──────┐ ┌──────┐        │
│  │终端  │ │网页搜索│ │文件  │        │
│  └──────┘ └──────┘ └──────┘        │
│  ┌──────┐ ┌──────┐ ┌──────┐        │
│  │Subagent│ │语音  │ │多Agent│       │
│  └──────┘ └──────┘ └──────┘        │
├─────────────────────────────────────┤
│         模型层（Model）              │
│   DeepSeek / OpenAI / Claude / 本地 │
├─────────────────────────────────────┤
│         运行环境（Runtime）          │
│   本地文件系统 / 沙箱 / Docker       │
└─────────────────────────────────────┘
```

### 四种工作模式

| 模式 | 适合场景 | 说明 |
|------|---------|------|
| **标准模式** | 大多数任务 | 最通用，普通人最容易理解 |
| **PTC 模式** | 批量处理 | 模型先写小段程序，再批量调用工具 |
| **极简模式** | 开发者 | 只用终端工具，最接近传统 Coding Agent |
| **创造模式** | 高级用户 | Agent 可以自己写插件、扩展功能 |

### 内置官方插件

| 插件 | 功能 |
|------|------|
| **终端** | 调用本机命令行，可限制超时和输出大小 |
| **网页搜索** | DeepSeek 自研搜索提供方 |
| **Subagent** | 子 Agent 递归，一个 Agent 可以拆多个小助手 |
| **Agent 循环** | 控制 Agent 怎么一轮轮调用工具 |
| **智能体团队** | 多 Agent 协作，共享任务看板（实验性） |
| **语音输入** | 本机调用 SenseVoice，语音转文字（实验性） |

---

## ⚡ 快速开始

### 前置要求

- Node.js 18+
- DeepSeek API Key（https://platform.deepseek.com/api_keys）

### 一行命令启动（官方 Web 版）

```bash
npx @deepseek-ai/dsh web
```

启动后自动打开浏览器，访问 `http://127.0.0.1:3080`

### 从源码编译

```bash
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

---

## 📚 新手入门教程

### 第一步：配置 API Key

1. 打开 DeepSeek 开放平台：https://platform.deepseek.com/
2. 注册账号，创建 API Key
3. 在 Harness 的 Settings → Models 里填入 API Key

### 第二步：选工作区

选一个本地文件夹作为工作目录，Harness 会在这个文件夹里读写文件、执行命令。

### 第三步：试第一个任务

在对话框里输入：

```
帮我分析这个文件夹里有哪些文件，写一个 README.md 总结
```

Harness 会自动：
1. 调用终端工具列出文件
2. 读取文件内容
3. 生成 README.md
4. 写回到工作目录

---

## 💻 核心示例

### 示例 1：自动整理文件夹

```
任务：帮我整理这个下载文件夹，按文件类型分类到不同子文件夹
```

**Harness 执行流程：**
```
1. 终端 → ls 列出所有文件
2. 终端 → file 查看文件类型
3. 终端 → mkdir 创建分类文件夹
4. 终端 → mv 移动文件
5. 写一个整理报告
```

### 示例 2：写一个 Python 爬虫

```
任务：帮我写一个爬取豆瓣电影 Top250 的 Python 脚本，保存成 CSV
```

**Harness 执行流程：**
```
1. 终端 → 检查 Python 环境
2. 终端 → pip install requests beautifulsoup4
3. 写代码 → scraper.py
4. 运行 → python scraper.py
5. 调试 → 修复报错
6. 输出 → douban_top250.csv
```

### 示例 3：多 Agent 协作

```
任务：做一个技术选型报告，对比 React 和 Vue
```

**多 Agent 分工：**
```
主 Agent（项目经理）
├── 子 Agent 1：调研 React 优缺点
├── 子 Agent 2：调研 Vue 优缺点
├── 子 Agent 3：搜索最新招聘需求
└── 汇总 → 生成对比报告
```

---

## 📥 下载地址

### 官方桌面版（内测中）

> ⚠️ 官方还没正式官宣，目前是 nightly 测试版
> 
> ✅ 已确认是官方签名，安全可信

| 平台 | 状态 | 下载地址 | 说明 |
|------|------|---------|------|
| macOS (Apple Silicon) | ✅ 有 | 官方 Telegram/社群分发 | 官方签名，已公证 |
| macOS (Intel) | ✅ 有 | 官方 Telegram/社群分发 | 官方签名 |
| Windows | ✅ 有 | 社区流传安装包 | 可正常使用 |
| Linux | ❌ 暂不支持 | - | 等官方后续更新 |

**官方仓库**：https://github.com/deepseek-ai/deepseek-harness

---

## 📂 本仓库包含的内容

```
deepseek-lab/
├── README.md                 # 本文件，详细介绍
├── examples/
│   └── quick-start.md        # 5 分钟快速上手
└── upstream/
    └── deepseek-harness/     # 官方源码（浅克隆）
        ├── apps/             # 应用（CLI、Web UI）
        ├── packages/         # 核心包
        ├── plugins/          # 官方插件
        └── docs/             # 官方文档
```

---

## 📊 DSec：背后的沙箱基础设施

DSec（DeepSeek Elastic Compute）是 DeepSeek 用来训练 Agent 的沙箱平台。

| 指标 | 数字 |
|------|------|
| 每天服务沙箱实例 | 300 万个 |
| 峰值并发 | 38 万个 |
| 创建速率 | 5000 个/秒 |
| 单节点容器数 | 3200 个 |

### 四种沙箱后端

| 类型 | 适合场景 | 隔离强度 |
|------|---------|---------|
| **FnCall** | OJ 判题、短任务 | 最弱 |
| **容器** | 软件工程类任务 | 中等 |
| **Firecracker microVM** | 安全类任务 | 强 |
| **完整 VM** | computer-use、移动端 | 最强 |

---

## 🤝 贡献

欢迎 PR 和 Issue！

- 官方仓库：https://github.com/deepseek-ai/deepseek-harness
- 插件话题：https://github.com/topics/dsh-plugin

---

## 📄 License

MIT License，可自由使用、修改、商用。
