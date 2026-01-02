# Trending Hub 🔥

![Build Status](https://github.com/zxc76o/trending-hub/actions/workflows/fetch-trending.yml/badge.svg)

多平台社交媒体热点聚合工具，支持 X/Twitter、TikTok、Bilibili、YouTube、Instagram、微博、知乎、百度、抖音等平台。

## 特性

- 🔄 **每30分钟自动更新** - 通过 GitHub Actions 定时抓取
- 🌐 **多平台支持** - 覆盖国内外主流社交媒体
- 📱 **响应式设计** - 支持桌面和移动端
- 🆓 **完全免费** - 使用 GitHub Pages 托管
- 🔓 **开源** - 可自定义和扩展

## 支持的平台

| 平台 | 数据源 | 状态 |
|------|--------|------|
| X (Twitter) | trends24.in | ✅ |
| TikTok | tokboard.com | ✅ |
| Bilibili | RSSHub | ✅ |
| YouTube | RSSHub | ✅ |
| Instagram | top-hashtags.com | ✅ |
| 微博 | RSSHub | ✅ |
| 知乎 | RSSHub | ✅ |
| 百度热搜 | 百度 API | ✅ |
| 抖音 | RSSHub | ✅ |

## 快速开始

### 1. Fork 本仓库

点击右上角 Fork 按钮

### 2. 启用 GitHub Pages

1. 进入仓库 Settings → Pages
2. Source 选择 "GitHub Actions"

### 3. 启用 Actions

1. 进入仓库 Actions 页面
2. 点击 "I understand my workflows, go ahead and enable them"

### 4. 手动触发首次运行

1. 进入 Actions → "Fetch Trending Topics"
2. 点击 "Run workflow"

几分钟后，访问 `https://你的用户名.github.io/trending-hub/` 查看效果。

## 本地开发

```bash
# 克隆仓库
git clone https://github.com/你的用户名/trending-hub.git
cd trending-hub

# 安装依赖
npm install

# 抓取数据
npm run fetch

# 构建 HTML
npm run build

# 本地预览
npm run dev
```

## 项目结构

```
trending-hub/
├── .github/
│   └── workflows/
│       └── fetch-trending.yml  # GitHub Actions 工作流
├── scripts/
│   ├── fetch-trending.js       # 数据抓取脚本
│   └── build-html.js           # HTML 生成脚本
├── data/
│   └── trending.json           # 抓取的热点数据
├── public/
│   └── index.html              # 生成的网页
├── package.json
└── README.md
```

## 自定义配置

### 修改 RSSHub 实例

编辑 `scripts/fetch-trending.js` 中的 `RSSHUB_INSTANCES` 数组：

```javascript
const RSSHUB_INSTANCES = [
  'https://rsshub.app',
  'https://你的自建实例.com',
];
```

### 添加新平台

在 `scripts/fetch-trending.js` 中添加抓取函数，然后在 `main()` 函数中调用。

### 修改更新频率

编辑 `.github/workflows/fetch-trending.yml` 中的 cron 表达式：

```yaml
schedule:
  - cron: '*/30 * * * *'  # 每30分钟
  # - cron: '0 * * * *'   # 每小时
  # - cron: '0 */2 * * *' # 每2小时
```

## API 使用

抓取的数据存储在 `data/trending.json`，可通过以下 URL 访问：

```
https://你的用户名.github.io/trending-hub/data/trending.json
```

JSON 结构：

```json
{
  "lastUpdated": "2024-01-01T00:00:00.000Z",
  "platforms": {
    "twitter": {
      "name": "X (Twitter)",
      "icon": "𝕏",
      "items": [
        {
          "rank": 1,
          "title": "热门话题",
          "url": "https://...",
          "hot": "",
          "platform": "twitter"
        }
      ]
    }
  }
}
```

## 注意事项

1. **请求频率限制** - 部分数据源可能有访问限制，建议使用自建 RSSHub 实例
2. **数据准确性** - 热点数据来自第三方，可能存在延迟或不完整
3. **GitHub Actions 限制** - 免费账户每月有 2000 分钟限制

## License

MIT License
