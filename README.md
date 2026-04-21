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
<div align="center">
注册一键对接
【aiyiwei.vip】开发者和AI爱好者调用中转：100ms响应，1元开票，30+工具零改造
<p>claude code使用特价 Claude Code分组。 gpt使用codex专属分组和纯az分组。gemini使用gemini-cli分组 新增claude code4.7</p>
<p>限时特价分组，1毛到2毛每百万token gpt-5-nano-2025-08-07 专属养虾</p>
<p>看过来 👉https://aiyiwei.vip/register?aff=9RDC（尾部带个人邀请码，介意可删除尾部字母）</p>
<p>-官网 1-2折，534个全球模型统一管控。</p>
<p>-0.5元到0.7元人民币每刀</p>
<p>-最低1元起充，按需使用无现金流压力</p>
<p>-💼 财务合规无忧</p>
<p>-每笔充值均可开电子发票，最低 1元 起开</p>
<p>-注册就送 $0.2，每天签到领 $0.2-$1</p>
<p>-告别代充灰色渠道，审计直接过	</p>
<p>-🛠️ 30+企业工具一键接入，现有系统零改造</p>
<p>-Claude Code/Cline/Cursor企业部署 → 文档已备</p>
<p>常用龙虾文档:https://migxy8em66.apifox.cn/doc-8196816</p>
<p>-Claude Code → https://migxy8em66.apifox.cn/doc-8196820</p>
<p>-Cursor → https://migxy8em66.apifox.cn/doc-8196829</p>
<p>-Cline → https://migxy8em66.apifox.cn/doc-8196827</p>
<p>-等30多个代码和开发工具适配文档已备齐</p>
<p>-一个接口自动适配，标准OpenAI格式，现有代码改个base_url直接跑，1小时完成接入</p>
<p>-5分钟配通工具，满意再规模化——让AI基础设施像水电一样即开即用</p>
<p>-推广有邀请奖励：推广奖励支持支付宝提现</p>

</div>
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
