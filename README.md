# 📚 小说爬虫程序

> 一个功能完整的小说网站爬虫工具，支持笔趣阁等网站

**项目地址**: https://github.com/cccyyywqq/novel-crawler

---

## 📖 使用指南

### 🚀 快速开始

**完整的、手把手的使用教程请查看**: [使用指南](USAGE_GUIDE.md)

30秒快速上手：
```bash
git clone https://github.com/cccyyywqq/novel-crawler.git
cd novel-crawler
npm install
npm run add https://www.biqiuge.com/book/你的小说ID/
npm run crawl
```

---

## ✨ 功能特点

- ✅ **爬取章节内容** - 自动下载小说所有章节
- ✅ **保存到本地文件** - TXT格式，方便阅读
- ✅ **定时更新监控** - 每2小时自动检查更新
- ✅ **多小说管理** - 同时追踪多本小说
- ✅ **断点续爬** - 中断后自动跳过已下载章节
- ✅ **自动清理广告** - 智能去除干扰内容
- ✅ **友好的命令行界面** - 简单易用

---

## 📦 安装

### 前置要求

- Node.js >= 16
- npm 或 yarn

### 安装步骤

```bash
# 克隆项目
git clone https://github.com/cccyyywqq/novel-crawler.git

# 进入目录
cd novel-crawler

# 安装依赖
npm install

# 编译TypeScript
npm run build
```

---

## 🎯 使用方法

### 1️⃣ 添加小说

```bash
npm run add <小说目录页URL>
```

示例：
```bash
npm run add https://www.biqiuge.com/book/12345/
```

### 2️⃣ 查看小说列表

```bash
npm run list
```

### 3️⃣ 下载小说

```bash
# 下载所有小说
npm run crawl

# 下载指定小说
npm run crawl <小说ID>
```

### 4️⃣ 检查更新

```bash
npm run update
```

### 5️⃣ 启动定时更新服务

```bash
npm run start
```

服务会每2小时自动检查小说更新并下载新章节。

按 `Ctrl+C` 停止服务。

### 6️⃣ 移除小说

```bash
npm run remove <小说ID>
```

---

## 📚 详细教程

**请查看完整使用指南**: [USAGE_GUIDE.md](USAGE_GUIDE.md)

包含：
- 环境准备
- 详细步骤
- 功能说明
- 常见问题
- 高级技巧
- 故障排除

---

## 🌐 支持的网站

✅ 已测试可用：
- 笔趣阁 (www.biqiuge.com)
- 大多数笔趣阁类网站

💡 提示：只要URL格式为 `/book/数字/` 的目录页，基本都支持

---

## 📁 项目结构

```
novel-crawler/
├── src/
│   ├── crawlers/          # 爬虫核心
│   ├── models/            # 数据模型
│   ├── services/          # 服务层
│   ├── utils/             # 工具函数
│   └── index.ts           # 入口文件
├── novels/                # 小说存储目录
├── chapters/              # 章节元数据
├── config/                # 配置文件
├── package.json
├── tsconfig.json
├── README.md              # 本文件
├── QUICKSTART.md          # 快速开始
└── USAGE_GUIDE.md         # 详细使用指南 ⭐
```

---

## 💡 数据存储

- 小说信息：`config/novels.json`
- 章节列表：`chapters/<小说ID>.json`
- 章节内容：`novels/<小说名>/<章节名>.txt`

---

## 🔧 配置说明

### 修改下载速度

编辑 `src/services/downloader.ts`：
```typescript
private requestDelay: number = 1000;  // 毫秒
```

### 修改定时频率

编辑 `src/index.ts`：
```typescript
scheduler.startUpdateCheck('0 */2 * * *')  // cron表达式
```

---

## ❓ 常见问题

### Q: URL应该是什么格式？

A: 应该是小说目录页，格式如：`https://www.biqiuge.com/book/12345/`

### Q: 下载中断了怎么办？

A: 直接重新运行 `npm run crawl`，程序会自动跳过已下载的章节

### Q: 如何查看小说ID？

A: 运行 `npm run list`，输出中包含小说ID

**更多问题请查看**: [USAGE_GUIDE.md#常见问题](USAGE_GUIDE.md#常见问题)

---

## 🤝 贡献指南

欢迎贡献代码！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 提交 Pull Request

---

## 📄 许可证

MIT License

---

## ⚠️ 免责声明

本工具仅供学习交流使用，请勿用于商业用途。使用本工具下载的内容版权归原作者所有，请支持正版阅读。

---

## 📮 联系方式

- **GitHub**: https://github.com/cccyyywqq/novel-crawler
- **问题反馈**: https://github.com/cccyyywqq/novel-crawler/issues

---

**📚 想要详细的、手把手的使用教程？请查看 [使用指南](USAGE_GUIDE.md)**