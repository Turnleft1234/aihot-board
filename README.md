# AIHOT 私人看板

一个**纯静态、零依赖、零后端**的网页，把 [aihot.news](https://aihot.news) 的内容按**你关注的话题**重新聚合展示。

## 它能做什么
- **我的关注**：填入你关心的话题（如 `OpenAI, Anthropic, Agent, 安全对齐`），页面实时调用 aihot.news 公开 API，按话题过滤并去重汇总成私人信息流。
- **AI 热点榜**：直接渲染 aihot.news 的「AI 热点榜」（`/hot`），含热度（信源/参与者/信号）与排名。
- 关注话题、已读状态仅保存在**本机浏览器**（localStorage），换设备不同步。
- 支持时间窗（1/3/7 天）、自动刷新、隐藏已读。

## 为什么不需要后端
aihot.news 的公开 API 返回了 `Access-Control-Allow-Origin: *`，因此浏览器可以**直接跨域请求**，GitHub Pages 这类纯静态托管即可运行，无需任何代理或服务器。

- 关注内容：`GET https://aihot.news/api/v1/items?q=话题&window=7d`
- 热点榜：`GET https://aihot.news/api/v1/hot-topics`

> 接口为匿名只读，约 60 次/分钟限流；正常使用完全够用。

## 本地预览
```bash
cd aihot-board
python3 -m http.server 8080
# 浏览器打开 http://localhost:8080
```

## 部署（GitHub Pages）
把这个仓库推到 GitHub 后，在仓库 **Settings → Pages** 选择 `main` 分支根目录即可。
访问地址：`https://<你的用户名>.github.io/aihot-board/`

## 数据来源与版权
内容版权归各原始信源与 aihot.news 所有；本页仅做聚合展示，遵循 aihot.news 的公开 API 署名要求（`Data source: AIHOT`）。
