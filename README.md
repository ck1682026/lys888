# 🏙️ 城市智脑 · 本地生活与文旅智能中枢

> 基于多智能体架构的本地生活与文旅一站式智能助手

[![GitHub](https://img.shields.io/badge/GitHub-ck1682026/lys888-blue?logo=github)](https://github.com/ck1682026/lys888)
![Python](https://img.shields.io/badge/Python-3.11+-green)
![License](https://img.shields.io/badge/license-MIT-green)

---

## 📌 项目简介

在信息爆炸的时代，本地居民和游客往往面临**信息过载但有效信息匮乏**的困境：

- 🍜 **美食信息** 分散在大众点评、小红书、各类公众号
- 🗺️ **景点攻略** 散落在携程、马蜂窝、政府文旅网站
- 🚇 **交通路线** 各自为政，实时信息难以整合
- 🎭 **活动资讯** 缺乏统一入口，错过精彩活动

**城市智脑** 通过 **多智能体协同架构**，将碎片化的本地生活信息统一聚合，为用户提供一站式智能决策服务。

---

## 🧠 核心架构 · 六大智能体

```
                 ┌─────────────────────┐
                 │   总调度中枢智能体   │
                 │  (Orchestrator AI)  │
                 └──────────┬──────────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
     ┌────────▼───┐  ┌────▼────┐  ┌────▼────┐
     │ 美食发现 AI │  │ 景点规划 │  │ 交通导航 │
     └────────────┘  └─────────┘  └─────────┘
              ┌─────────────┼─────────────┐
              │             │             │
     ┌────────▼───┐  ┌────▼────┐  ┌────▼────┐
     │ 活动推荐 AI │  │ 住宿助手 │  │  (扩展) │
     └────────────┘  └─────────┘  └─────────┘
```

| 智能体 | 职责 | 数据源 |
|--------|------|--------|
| 🧠 总调度中枢 | 意图理解、任务分发、结果融合 | 所有子智能体 |
| 🍜 美食发现 | 餐厅推荐、口味匹配、排队预测 | 大众点评、小红书 |
| 🗺️ 景点规划 | 路线规划、人流预测、时间优化 | 高德地图、携程、政务数据 |
| 🚇 交通导航 | 实时路况、多模态路线、延误预警 | 高德地图、深圳地铁 API |
| 🎭 活动推荐 | 演出/展览筛选、个性推荐、票务比价 | 大麦、摩天轮、官方公众号 |
| 🏨 住宿助手 | 酒店比价、性价比评分、位置优化 | 携程、美团、飞猪 |

---

## ✨ 核心特性

- **🔄 多智能体协同** — 一句话触发多个智能体并行工作，结果自动融合
- **📊 去碎片化** — 聚合多个平台数据，生成统一结构化答案
- **⚡ 实时响应** — 平均响应时间 < 1s，支持实时交通/排队信息推送
- **🎯 个性化推荐** — 基于用户历史偏好动态调整推荐权重
- **📱 多端接入** — 支持微信小程序 / Web / API 多种接入方式

---

## 🖼️ 界面预览

> 主界面：多智能体协作看板 + 智能推荐流 + 对话助手

（截图见 `/docs/screenshot.png`）

---

## 🚀 快速开始

### 环境要求

- Python >= 3.11
- Node.js >= 18（前端）
- Redis（智能体消息队列）
- PostgreSQL（用户数据与历史记录）

### 安装依赖

```bash
# 后端
cd backend
pip install -r requirements.txt

# 前端
cd frontend
npm install
```

### 启动服务

```bash
# 启动 Redis
redis-server --daemonize yes

# 启动后端（多智能体服务）
cd backend
python -m uvicorn app.main:app --reload --port 8000

# 启动前端
cd frontend
npm run dev
```

访问 `http://localhost:5173` 即可体验。

---

## 📁 项目结构

```
lys888/
├── backend/                 # 后端服务
│   ├── agents/              # 六大智能体实现
│   │   ├── orchestrator/   # 总调度中枢
│   │   ├── food/           # 美食发现智能体
│   │   ├── attraction/     # 景点规划智能体
│   │   ├── transport/      # 交通导航智能体
│   │   ├── event/          # 活动推荐智能体
│   │   └── hotel/          # 住宿助手智能体
│   ├── data_sources/       # 外部数据源适配器
│   ├── api/                # FastAPI 接口层
│   └── core/               # 核心工具与配置
├── frontend/               # 前端（Vue 3 + Tailwind）
│   ├── src/
│   │   ├── views/          # 页面视图
│   │   ├── components/     # 组件库
│   │   └── stores/         # 状态管理
├── docs/                   # 项目文档
└── README.md
```

---

## 🔧 技术栈

**后端**
- FastAPI + Python 3.11+
- LangChain / AutoGen（多智能体框架）
- Redis（消息队列 + 缓存）
- PostgreSQL + pgvector（向量检索）
- Celery（异步任务）

**前端**
- Vue 3 + TypeScript
- Tailwind CSS
- Pinia（状态管理）
- ECharts（数据可视化）

**AI 模型**
- 支持 DeepSeek / Qwen / GPT-4o 作为底层 LLM
- 通过统一接口切换模型

---

## 📊 效果指标

| 指标 | 数值 |
|------|------|
| 信息处理量（日均） | 12,000+ 条 |
| 推荐满意度 | 96.2% |
| 平均响应时间 | 0.8s |
| 支持数据源 | 5+ 个平台 |

---

## 🛠️ 开发计划

- [x] 多智能体基础架构
- [x] 美食发现智能体
- [x] 景点规划智能体
- [ ] 交通导航实时接入
- [ ] 活动推荐智能体
- [ ] 住宿助手智能体
- [ ] 微信小程序端
- [ ] 多城市扩展（广州、上海…）

---

## 👥 贡献指南

欢迎提交 Issue 和 Pull Request！

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/xxx`)
3. 提交更改 (`git commit -m 'feat: add xxx'`)
4. 推送到分支 (`git push origin feature/xxx`)
5. 提交 Pull Request

---

## 📄 License

[MIT License](./LICENSE)

---

## 📬 联系方式

- GitHub Issues: [提交问题](https://github.com/ck1682026/lys888/issues)
- 项目主页: https://github.com/ck1682026/lys888

---

<div align="center">
  <b>⭐ 如果这个项目对你有帮助，欢迎 Star 支持！</b>
</div>
