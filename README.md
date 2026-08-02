# 🏋️ 破壁健身 · Breakthrough Fitness

> 个人健身训练追踪应用 · H5 网页版
> 🔗 **在线体验：https://xujianshu6-sketch.github.io/fitness-web/**

![破壁健身](screenshot_home.png)

---

## ✨ 功能亮点

- **核心动作库** —— 分类浏览 + 搜索，覆盖多肌群经典训练动作
- **2D SVG 肌肉图谱** —— 男 / 女双版本，训练目标肌群可视化
- **训练记录打卡** —— 记录组数 / 重量 / 次数，云端同步，换设备数据不丢
- **打卡热力图** —— 训练频率一目了然
- **能力雷达图** —— 基于训练容量的阶段性能力评估
- **健身知识库** —— 训练干货与动作指导
- **训练计划管理** —— 制定并跟踪你的训练计划
- **手机号登录** —— 首次自动注册，数据永久云端存储

## 🛠️ 技术栈

| 层 | 技术 |
|---|---|
| 前端框架 | **uni-app**（Vue 3 + Vite），一套代码多端运行 |
| 后端 | **uniCloud 云开发**（阿里云）：云函数 + 云数据库 |
| 部署 | **GitHub Pages**（静态托管，0 成本） |
| 数据 | 前端直连云端数据库（BaaS 模式），无自建服务器 |

## 🏗️ 架构

```text
┌──────────────┐         ┌──────────────────────┐
│  用户浏览器     │         │   GitHub Pages（海外）  │
│              │  ◄────  │   静态文件：HTML/JS/CSS │
│  uni-app H5  │         └──────────────────────┘
│              │         ┌──────────────────────┐
│              │  ◄────  │   uniCloud（阿里云机房）  │
└──────────────┘         │   云函数 + 云数据库     │
                         └──────────────────────┘
```

前后端分离：网页文件托管在 GitHub Pages，数据通过 HTTPS API 直连 uniCloud 云服务，两者互不依赖。

## 🚀 本地运行

1. 安装 [HBuilderX](https://www.dcloud.io/hbuilderx.html)（uni-app 官方 IDE）
2. 导入项目 → 关联你的 uniCloud 服务空间（阿里云版）
3. 菜单：**运行 → 运行到浏览器**

## 📦 部署到 GitHub Pages

1. **发行 → 网站-H5手机版**，部署域名填 `https://<用户名>.github.io/<仓库名>/`
2. `manifest.json` 配置 `h5.router.base = "/<仓库名>/"`（发行对话框不会自动写入！）
3. 上传 `unpackage/dist/build/web` 产物，**并在仓库根目录放一个空文件 `.nojekyll`**（否则 Pages 的 Jekyll 构建会失败）
4. 仓库 **Settings → Pages**：Source 选 `Deploy from a branch` → `main` + `/ (root)`

> 详细踩坑记录见配套知识库文档（h5.router.base、.nojekyll、uniCloud 跨域安全域名等）。

## 📁 项目结构

```text
├─ pages/               # 页面：首页、动作库、训练、计划、学院、我的
├─ components/          # 公共组件（肌肉图谱等）
├─ utils/               # 工具与 API 封装
├─ static/              # 静态资源（SVG、动作数据）
├─ uniCloud-aliyun/     # uniCloud 后端（云函数 + 数据库 Schema）
├─ raw_data/            # 原始数据处理脚本
└─ manifest.json        # 应用配置（含 h5 部署路径）
```

## 📄 说明

- 本仓库仅包含前端构建产物与展示文档，**源码保留在本地 HBuilderX 工程中**，不含任何用户数据
- 个人项目，学习交流用途。移动端 App 版本基于同一套代码（uni-app 跨端）构建

