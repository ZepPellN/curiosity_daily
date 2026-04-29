# Harness不是目的，知识才是护城河 —— 一个AI工程交付团队的知识沉淀实践

- **Source:** 微信公众号（腾讯程序员）
- **Author:** stevenpxiao
- **Date:** 2026-04-27
- **Link:** https://mp.weixin.qq.com/s/Xy8NwrHZRWv301eTZz4Dpw
- **Type:** article

---

> 当 Harness Engineering 成为 2026 年最热门的 AI 工程话题，业界争论焦点集中在"该用多大的模型"还是"该搭多复杂的工作流"时，我们团队在落地实践中发现了一个被低估的事实——**构建 Harness 工作流不是最终目的，私域和团队知识的沉淀才是真正的技术护城河**。

## 核心论点

**Skill、Agent、工具链会随模型迭代更新，但领域知识是永恒的。** 工作流是手段，知识是目的。

## 知识体系架构：三维正交

### 五层存储
| Layer | 名称 | 范围 |
|-------|------|------|
| 0-P | 个人偏好 | 纯本地，不共享 |
| 0-T | 团队约定 | 团队级，Git 共享 |
| 1 | 技术知识 | 团队级，跨项目 |
| 2 | 业务知识 | 团队级，按领域 |
| 3 | 项目知识 | 项目级，随项目走 |

知识可以"向上提升"：Layer 3 → 判定为跨项目通用 → 自动提升到 Layer 1/2

### 五种知识类型（MECE）
- **model** — 实体定义、数据结构、关系图
- **decision** — 技术选型、架构决策及理由
- **guideline** — 推荐做法 (recommend) / 禁止做法 (avoid)
- **pitfall** — 已知风险、故障模式、排查步骤
- **process** — 业务流程、状态机、操作步骤

### 三级成熟度 + 自动衰减
```
draft → verified (1 项目验证) → proven (≥2 项目验证)
```
- proven 12 月未引用 → 降级 verified
- verified 6 月未引用 → 降级 draft
- draft 持续未引用 + Lint → 归档

## 三级渐进式索引（类比 Karpathy LLM Wiki）

| Layer | 文件 | 大小 | 作用 |
|-------|------|------|------|
| A: 全景目录 | knowledge-catalog.md | ~50行 | "知识库有什么？" |
| B: 分类清单 | catalog.md | ~100-300行 | "这分类有哪些条目？" 一行摘要 |
| C: 完整条目 | TK-*.md / BK-*.md | ~50-200行 | 完整内容 + 背景 + 适用场景 |

Agent 用 ~50 行了解全貌，~300 行定位，按需读取完整条目。对比"一次性推送 50 条知识"（5000-10000 行），效率提升一个数量级。

## 工作流 = 知识流动的管道

三个关键时刻：
1. **INIT** — git pull 团队知识仓库，注入 Agent 查询入口
2. **各阶段执行** — Agent 在决策点按需查询知识库
3. **ARCHIVE** — 自动从全流程产物提取知识条目（decision/pitfall/guideline），执行提升判定

## 远程操控：突破人机交互瓶颈

传统假设（人坐在 IDE 前随时响应）→ 实际一天只有 4 小时能操控 Agent。

方案：手机远程接管开发机上运行的 AI 编程会话
- **跨设备会话接管** — 手机/平板/电脑均可
- **异步审批** — Agent 提交产物暂停等待，人随时审批
- **通知触达** — 企业微信主动推送关键节点

核心设计原则：**文件系统即状态机** — 所有状态持久化在文件中，从任意设备接入看到一致状态。

## 与个人知识管理的对应

这篇文章的体系可以 1:1 映射到个人 Harness 工程：
- Layer 0-P ↔ CLAUDE.md（个人偏好）
- Layer 1 ↔ wiki/（技术知识）
- 三级索引 ↔ wiki/index.md → section overview → 单页
- 成熟度 ↔ candidate → mature（wiki-absorb 的 promote 机制）
- ARCHIVE ↔ wiki-absorb 的自动提取和链接
- Lint ↔ wiki-lint / wiki-rebuild-index
