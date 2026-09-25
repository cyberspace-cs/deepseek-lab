# 🚀 5 分钟快速上手

## 1. 安装 Node.js

去 https://nodejs.org/ 下载 LTS 版本，一路下一步安装。

验证安装：
```bash
node -v
npm -v
```

## 2. 获取 DeepSeek API Key

1. 打开 https://platform.deepseek.com/
2. 注册账号
3. 左侧菜单 → API Keys
4. 创建新的 API Key，复制保存

## 3. 启动 Harness

```bash
npx @deepseek-ai/dsh web
```

第一次运行会自动下载依赖，等几分钟。

启动后会自动打开浏览器，访问 `http://127.0.0.1:3080`

## 4. 配置 API Key

1. 点左下角 Settings
2. 选 Models
3. 填入你的 DeepSeek API Key
4. 保存

## 5. 试第一个任务

在输入框里输入：

```
帮我在当前文件夹创建一个 hello.py，打印 Hello World，然后运行它
```

看看 Harness 怎么自动完成！

---

## 🎯 推荐新手试的 10 个任务

1. `帮我整理这个文件夹，按文件类型分类`
2. `写一个 Python 脚本，爬取天气预报`
3. `分析这个文件夹里的代码，画一个架构图`
4. `帮我写一个简历模板 Word 文档`
5. `下载这篇文章 https://example.com ，总结成 3 句话`
6. `把这个文件夹里所有 .md 文件改成大写文件名`
7. `写一个贪吃蛇小游戏，用 HTML 单文件`
8. `帮我查一下今天北京的天气，然后写个穿衣建议`
9. `分析这个 CSV 文件，画个柱状图`
10. `帮我写一个微信公众号文章，主题是 AI Agent 入门`

---

## 🐛 常见问题

### Q: npx 命令报错怎么办？
A: 确保 Node.js 版本 >= 18，或者先运行 `npm install -g @deepseek-ai/dsh`

### Q: 怎么切换模型？
A: Settings → Models → 选 DeepSeek-V3 或 DeepSeek-R1

### Q: 支持本地模型吗？
A: 支持，在 Settings → Models 里填 Ollama 或 vLLM 的地址

### Q: 怎么装插件？
A: 在插件市场搜索，或者手动放插件文件到 `~/.dsh/plugins/`
