# 小说爬虫使用指南

> 一份完整的、手把手的使用教程

## 📖 目录

- [快速开始](#快速开始)
- [详细教程](#详细教程)
- [功能说明](#功能说明)
- [常见问题](#常见问题)
- [高级技巧](#高级技巧)
- [故障排除](#故障排除)

---

## 快速开始

### 30秒快速上手

```bash
# 1. 克隆项目
git clone https://github.com/cccyyywqq/novel-crawler.git
cd novel-crawler

# 2. 安装依赖
npm install

# 3. 添加小说（替换为真实URL）
npm run add https://www.biqiuge.com/book/你的小说ID/

# 4. 开始下载
npm run crawl
```

下载的小说会保存在 `novels/小说名/` 目录下。

---

## 详细教程

### 第一步：环境准备

#### 1.1 检查Node.js

确保你的电脑已安装Node.js（版本 >= 16）：

```bash
node --version
```

如果未安装：
- **macOS**: `brew install node`
- **Windows**: 访问 https://nodejs.org 下载安装
- **Linux**: 
  ```bash
  curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
  sudo apt-get install -y nodejs
  ```

#### 1.2 获取项目

**方式一：克隆仓库**
```bash
git clone https://github.com/cccyyywqq/novel-crawler.git
cd novel-crawler
```

**方式二：下载ZIP**
1. 访问 https://github.com/cccyyywqq/novel-crawler
2. 点击 "Code" -> "Download ZIP"
3. 解压并进入目录

#### 1.3 安装依赖

```bash
npm install
```

等待安装完成，通常需要1-2分钟。

---

### 第二步：找到小说URL

#### 2.1 支持的网站

✅ **已测试可用的网站**：
- https://www.biqiuge.com （笔趣阁）
- 大多数笔趣阁类网站

🔍 **查找更多笔趣阁网站**：
在搜索引擎搜索 "笔趣阁" 即可找到。

#### 2.2 获取正确的URL

**正确示例**（目录页）：
```
✅ https://www.biqiuge.com/book/12345/
   这是小说的目录页，显示所有章节列表
   
✅ https://www.biquge.com/book/67890/
   同样是目录页格式
```

**错误示例**：
```
❌ https://www.biqiuge.com/book/12345/1.html
   这是章节内容页，不是目录页
   
❌ https://www.biqiuge.com/search.php?q=斗破苍穹
   这是搜索结果页
```

**如何确认是正确的URL？**
1. 打开页面应该显示小说名称、作者、简介
2. 页面下方应该有完整的章节列表（几十到几千章）
3. URL格式通常是 `/book/数字/`

---

### 第三步：添加小说

#### 3.1 添加第一本小说

```bash
npm run add https://www.biqiuge.com/book/12345/
```

**预期输出**：
```
正在获取小说信息: https://www.biqiuge.com/book/12345/
小说添加成功: 斗破苍穹 (共1648章)
```

#### 3.2 查看已添加的小说

```bash
npm run list
```

**输出示例**：
```
追踪的小说列表:
================================================================================
ID: aHR0cHM6Ly93d3cuYmlxdWl1Z2UuY29tL2Jvb2svMTIzNDUv
名称: 斗破苍穹
作者: 天蚕土豆
章节: 1648
状态: 已完结
最后更新: 2024-03-24
--------------------------------------------------------------------------------
```

#### 3.3 添加更多小说

重复添加命令即可：
```bash
npm run add https://www.biqiuge.com/book/23456/
npm run add https://www.biqiuge.com/book/34567/
```

---

### 第四步：下载小说

#### 4.1 下载所有小说

```bash
npm run crawl
```

**下载过程**：
```
开始下载: 斗破苍穹
总章节: 1648

[1/1648] 正在下载: 第一章 陨落的天才
[2/1648] 正在下载: 第二章 斗之气三段
[3/1648] 正在下载: 第三章 客人
...
[10/1648] 正在下载: 第十章 神秘的老者

已下载 10 章，进度: 0.6%
```

#### 4.2 下载指定小说

使用小说ID：
```bash
npm run crawl aHR0cHM6Ly93d3cuYmlxdWl1Z2UuY29tL2Jvb2svMTIzNDUv
```

#### 4.3 断点续传

如果下载中断（网络问题、关闭终端等），直接重新运行：
```bash
npm run crawl
```

程序会自动跳过已下载的章节：
```
[1/1648] 跳过已下载: 第一章 陨落的天才
[2/1648] 跳过已下载: 第二章 斗之气三段
[3/1648] 正在下载: 第三章 客人  <- 从这里继续
```

---

### 第五步：查看下载结果

#### 5.1 文件位置

```
novel-crawler/
└── novels/
    └── 斗破苍穹/
        ├── 第一章 陨落的天才.txt
        ├── 第二章 斗之气三段.txt
        ├── 第三章 客人.txt
        └── ...
```

#### 5.2 阅读章节

**方式一：直接打开**
```bash
# macOS
open novels/斗破苍穹/第一章\ 陨落的天才.txt

# Linux
cat novels/斗破苍穹/第一章\ 陨落的天才.txt

# Windows
notepad novels/斗破苍穹/第一章 陨落的天才.txt
```

**方式二：使用阅读器**
- 将 `novels/斗破苍穹/` 文件夹导入到电子书阅读器
- 支持的阅读器：Kindle、iBooks、Calibre等

---

## 功能说明

### 1. 添加小说 (npm run add)

**用途**：将小说添加到追踪列表

**参数**：小说目录页URL

**示例**：
```bash
npm run add https://www.biqiuge.com/book/12345/
```

**作用**：
- 提取小说名称、作者、状态
- 获取所有章节列表
- 保存到配置文件

---

### 2. 查看列表 (npm run list)

**用途**：查看所有已添加的小说

**示例**：
```bash
npm run list
```

**输出信息**：
- 小说ID
- 名称和作者
- 总章节数
- 连载状态
- 最后更新时间

---

### 3. 下载小说 (npm run crawl)

**用途**：下载小说章节

**参数**：可选的小说ID

**示例**：
```bash
# 下载所有
npm run crawl

# 下载指定
npm run crawl <小说ID>
```

**特性**：
- 自动跳过已下载章节
- 每10章自动保存进度
- 失败章节自动重试

---

### 4. 检查更新 (npm run update)

**用途**：检查小说是否有新章节

**示例**：
```bash
npm run update
```

**工作流程**：
1. 访问小说目录页
2. 对比章节数量
3. 如果有新章节，自动下载

**适用场景**：
- 追连载小说
- 定期检查更新

---

### 5. 启动定时服务 (npm run start)

**用途**：后台自动检查更新

**示例**：
```bash
npm run start
```

**工作方式**：
- 每2小时自动检查一次
- 发现新章节自动下载
- 按 `Ctrl+C` 停止

**后台运行**（推荐）：
```bash
# macOS/Linux
nohup npm run start > crawler.log 2>&1 &

# 查看日志
tail -f crawler.log

# 停止服务
ps aux | grep node
kill <进程ID>
```

---

### 6. 移除小说 (npm run remove)

**用途**：从追踪列表移除小说

**参数**：小说ID

**示例**：
```bash
npm run remove aHR0cHM6Ly93d3cuYmlxdWl1Z2UuY29tL2Jvb2svMTIzNDUv
```

**注意**：
- 只移除追踪，不删除已下载的章节
- 已下载的TXT文件会保留

---

## 常见问题

### Q1: 提示 "网络错误" 或 "无法访问"

**原因**：
- 网站不可访问
- 网络连接问题
- 网站有反爬限制

**解决方法**：
1. 检查网站是否能正常访问
2. 尝试其他笔趣阁网站
3. 等待几分钟后重试

---

### Q2: 下载的章节内容有乱码

**原因**：网站编码问题

**解决方法**：
已在程序中处理UTF-8编码，如仍有问题：
1. 尝试其他网站
2. 使用文本编辑器转换编码

---

### Q3: 下载速度太慢

**原因**：程序默认每章间隔1秒，防止被封

**调整方法**：

编辑 `src/services/downloader.ts`：
```typescript
private requestDelay: number = 1000;  // 改为500更快
```

重新编译：
```bash
npm run build
```

⚠️ **警告**：间隔太短可能导致IP被封

---

### Q4: 如何修改下载目录？

**方法**：

编辑 `src/index.ts`：
```typescript
const baseDir = '/你的/自定义/路径';
```

重新编译：
```bash
npm run build
```

---

### Q5: 如何查看小说ID？

运行：
```bash
npm run list
```

输出中的 `ID: xxxxx` 就是小说ID。

---

### Q6: 支持其他网站吗？

**支持**：大多数笔趣阁类网站

**测试方法**：
1. 尝试添加：`npm run add <URL>`
2. 如果能成功添加，说明支持

**扩展其他网站**：
继承 `BaseCrawler` 类，实现三个方法即可。

---

## 高级技巧

### 技巧1：批量添加小说

创建脚本 `batch-add.sh`：
```bash
#!/bin/bash
# 批量添加小说

urls=(
  "https://www.biqiuge.com/book/12345/"
  "https://www.biqiuge.com/book/23456/"
  "https://www.biqiuge.com/book/34567/"
)

for url in "${urls[@]}"; do
  echo "添加: $url"
  npm run add "$url"
  sleep 2
done

echo "批量添加完成"
```

运行：
```bash
chmod +x batch-add.sh
./batch-add.sh
```

---

### 技巧2：只下载最新章节

查看已下载章节数：
```bash
npm run list
```

假设显示：总章节1650，上次下载到1640章

下载新增章节：
```bash
npm run update
```

---

### 技巧3：定时下载（系统级）

**macOS/Linux - 使用crontab**：
```bash
# 编辑定时任务
crontab -e

# 添加以下内容（每天凌晨2点运行）
0 2 * * * cd ~/novel-crawler && npm run update >> update.log 2>&1
```

**Windows - 使用任务计划程序**：
1. 打开"任务计划程序"
2. 创建基本任务
3. 设置触发器：每天
4. 操作：启动程序
   - 程序：`node`
   - 参数：`dist/index.js update`
   - 起始位置：`C:\path\to\novel-crawler`

---

### 技巧4：导出为电子书

使用Calibre转换：

1. 安装Calibre：https://calibre-ebook.com/
2. 将TXT文件导入Calibre
3. 转换为EPUB、MOBI等格式

---

### 技巧5：多线程下载（高级）

修改 `src/services/downloader.ts`：
```typescript
import { PromisePool } from 'async-pool';

async downloadWithPool(novelId: string) {
  const chapters = await this.getChapters(novelId);
  const pool = new PromisePool(5); // 5个并发
  
  await pool.map(chapters, async (chapter) => {
    await this.downloadChapter(chapter);
  });
}
```

---

## 故障排除

### 问题1：npm install 失败

**错误**：网络超时或权限问题

**解决**：
```bash
# 清除缓存
npm cache clean --force

# 使用国内镜像
npm config set registry https://registry.npmmirror.com

# 重新安装
npm install
```

---

### 问题2：git clone 失败

**错误**：连接超时

**解决**：
```bash
# 使用国内镜像
git clone https://github.com.cnpmjs.org/cccyyywqq/novel-crawler.git

# 或下载ZIP
# 访问 https://github.com/cccyyywqq/novel-crawler
# 点击 Code -> Download ZIP
```

---

### 问题3：运行报错 "Cannot find module"

**解决**：
```bash
# 确保在项目目录
cd ~/novel-crawler

# 重新安装依赖
rm -rf node_modules package-lock.json
npm install

# 重新编译
npm run build
```

---

### 问题4：下载卡住不动

**原因**：网络问题或网站限流

**解决**：
1. 按 `Ctrl+C` 停止
2. 检查网络连接
3. 等待几分钟后重新运行 `npm run crawl`

程序会自动跳过已下载章节。

---

### 问题5：章节内容为空

**原因**：网站结构不同

**解决**：
检查是否为支持的网站，或查看控制台错误信息。

---

## 数据文件说明

### config/novels.json
存储所有追踪的小说信息：
```json
{
  "novels": [
    {
      "id": "xxx",
      "name": "小说名称",
      "author": "作者",
      "url": "URL",
      "totalChapters": 1648,
      "status": "completed"
    }
  ]
}
```

### chapters/<ID>.json
存储小说的章节列表：
```json
{
  "novelId": "xxx",
  "chapters": [
    {
      "index": 0,
      "title": "第一章",
      "url": "https://...",
      "crawled": true,
      "crawledAt": "2024-03-24T..."
    }
  ]
}
```

### novels/<小说名>/
存储章节内容（TXT格式）：
```
第一章.txt
第二章.txt
...
```

---

## 更新日志

### v1.0.0 (2024-03-24)
- ✨ 初始版本发布
- ✨ 支持笔趣阁类网站
- ✨ 自动下载章节
- ✨ 定时更新监控
- ✨ 断点续传
- ✨ 多小说管理

---

## 贡献指南

欢迎贡献代码！

1. Fork 本仓库
2. 创建特性分支：`git checkout -b feature/AmazingFeature`
3. 提交更改：`git commit -m 'Add some AmazingFeature'`
4. 推送到分支：`git push origin feature/AmazingFeature`
5. 提交 Pull Request

---

## 许可证

MIT License - 可自由使用、修改和分发

---

## 联系方式

- GitHub: https://github.com/cccyyywqq/novel-crawler
- 问题反馈: https://github.com/cccyyywqq/novel-crawler/issues

---

## 免责声明

本工具仅供学习交流使用，请勿用于商业用途。使用本工具下载的内容版权归原作者所有，请支持正版阅读。

---

**祝你使用愉快！如有问题请查看 [常见问题](#常见问题) 或提交 Issue。**