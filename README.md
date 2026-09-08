# 公司官网落地页开发（首页 + 关于页）

> 实习项目
· 官网链接：https://aihub.ssturing.com

## 基本信息

| 项目类型 | 我的角色 | 当前状态 |
|----------|----------|----------|
| 企业项目 | 独立开发 | ✅ 已上线并嵌入公司后台 |

## 技术栈

Tailwind CSS / 原生 JavaScript / postMessage / Docker / Cloudflare Pages

## 项目概述

为公司官网开发首页和关于页，需要同时支持**独立访问**和 **iframe 嵌入公司 new-api 后台**两种部署方式。核心挑战是解决 iframe 嵌入场景下的多个兼容性问题。

## 核心功能

- Hero 区域**视频背景** + 滚动切换第二屏内容
- **浅色/深色主题**自动切换（适配系统 `prefers-color-scheme`）
- 自定义光标跟随（lime 色圆点，`mix-blend-difference`）
- 滚动触发渐入动画（IntersectionObserver）
- 3D 卡片堆叠展示 + 鼠标视差效果
- 数字滚动计数动画
- 无障碍适配（`prefers-reduced-motion`）

## 核心技术难点与解决方案

| 难点 | 解决方案 |
|------|----------|
| **iframe 主题无法跟随父窗口** | 落地页通过 `postMessage` 监听父窗口主题消息（兼容 3 种消息格式），动态切换 CSS 变量 |
| **iframe 底部白色空隙** | 落地页通过 `postMessage` 主动上报内容高度，父窗口动态设置 iframe 高度 |
| **导航栏在视频背景上不可读** | 采用磨砂玻璃胶囊条方案（`bg-black/20` + `backdrop-blur-xl` + 白色文字） |
| **iframe sandbox 限制 localStorage** | 所有 `localStorage` 操作用 `try/catch` 包裹，安全降级 |
| **外部链接在 iframe 内无法跳转** | 添加 `target="_blank" rel="noopener noreferrer"` |

## 部署方案

- **前端代码**：推送到 GitHub，Cloudflare Pages 自动部署
- **后台集成**：修改 new-api 后台（Docker 自定义构建），实现主题消息下发与高度监听
- **回滚方案**：`docker-compose.yml` 改回 `latest` 标签即可

## 我的贡献

- 独立完成全部前端开发（UI 设计、交互实现、主题系统）
- 独立排查并解决 iframe 嵌入场景下的所有兼容问题
- 编写 `new-api-changes.md` 改动说明文档，交付团队维护

## 相关链接

- [作品集总览](https://github.com/G4Zzhe/G4Zzhe)
