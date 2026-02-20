# 项目开发方法论

> 适用于所有新项目。定义目录结构、文件命名、开发流程。

## 目录结构规范

```
project-name/
├── CLAUDE.md               # AI 辅助开发指令（项目级）
├── docs/                   # 所有文档
│   ├── product-design.md   # 产品设计文档（功能、用户、场景、界面）
│   ├── tech-architecture.md# 技术架构文档（技术栈、模块划分、数据流）
│   ├── visual-standard.md  # 视觉交互设计标准（色彩、字体、间距、组件）
│   ├── project-progress.md # 迭代计划与进度跟踪
│   ├── marketing-posts.md  # 社交媒体宣传素材
│   ├── visual-prototype.html # 视觉原型（可浏览器打开预览）
│   ├── plans/              # 设计方案文档（brainstorming 产出）
│   └── scripts/            # 构建/部署辅助脚本
├── code/                   # 应用源码（前端 + 后端）
├── home/                   # 产品官网 / Landing Page
├── worker/                 # 云函数 / 后端服务
└── deploy/                 # 部署配置（CI/CD、Docker 等）
```

## 核心文件命名规格

| 文件 | 用途 | 必须 |
|------|------|------|
| `CLAUDE.md` | AI 开发指令：项目结构、技术决策、开发命令 | ✅ |
| `docs/product-design.md` | 产品定位、目标用户、核心场景、界面布局、功能清单 | ✅ |
| `docs/tech-architecture.md` | 技术栈选型、架构图、模块职责、数据流、API 设计 | ✅ |
| `docs/visual-standard.md` | Design Tokens、色彩系统、字体、间距、组件规范 | ✅ |
| `docs/visual-prototype.html` | 单文件 HTML 视觉原型，浏览器直接打开预览 | ✅ |
| `docs/project-progress.md` | 分阶段迭代计划，每阶段有明确产出和状态 | ✅ |
| `docs/marketing-posts.md` | 产品 Slogan、一句话介绍、社交媒体发布素材 | 可选 |

## 项目启动流程（按顺序执行）

### Phase 0: 头脑风暴
- 明确要解决的问题和目标用户
- 讨论核心功能边界（做什么、不做什么）
- 确定产品形态（桌面应用 / Web / 移动端 / CLI）
- 确定商业模式（免费 / Freemium / 付费）
- 产出：想法整理，进入下一阶段的共识

### Phase 1: 产品设计文档
- 写 `docs/product-design.md`
- 包含：产品定位、目标用户画像、核心用户场景、界面布局（ASCII 图）、功能清单、交互细节
- 所有功能细节在此阶段确定，不留模糊地带
- 确认支持的平台（macOS / Windows / Linux / Web / iOS / Android）

### Phase 2: 技术架构文档
- 写 `docs/tech-architecture.md`
- 包含：技术栈选型及理由、架构图、模块划分、数据流、API 设计、第三方依赖
- 关键技术决策记录（选了什么、为什么、放弃了什么）

### Phase 3: 视觉标准确认
- 写 `docs/visual-standard.md`
- 包含：Design Tokens（颜色、字体、间距、圆角、阴影）、组件规范、响应式规则、暗色模式
- 基于视觉标准制作 `docs/visual-prototype.html`（单文件，浏览器可直接预览）

### Phase 4: 品牌定义
- 产品名称确定
- Slogan 确定
- 应用 ICON 设计
- Landing Page 设计（`home/index.html`）
- 写 `docs/marketing-posts.md`（可选，用于产品发布宣传）

### Phase 5: 迭代计划
- 写 `docs/project-progress.md`
- 按阶段拆分：Phase 0 → Phase N，每阶段有明确目标和产出
- 从 MVP 开始，逐步迭代增强
- 每阶段完成后更新状态

### Phase 6: 按计划实施
- 按 `project-progress.md` 的阶段顺序开发
- 每完成一个阶段，更新进度文档
- 写 `CLAUDE.md` 记录项目上下文和关键设计决策

## 文档维护规范

每次完成一个功能或阶段后，必须同步更新相关文档：

1. `docs/project-progress.md` — 更新阶段状态，补充已完成内容
2. `docs/product-design.md` — 新增功能写入功能清单，变更设计同步更新
3. `docs/tech-architecture.md` — 新增模块、技术选型变更、存储路径变更同步更新
4. `CLAUDE.md` — 新增关键设计决策、新增命令、新增存储路径
5. 删除过时内容 — 已废弃的方案、已移除的功能、不再适用的说明，直接删除而非注释保留
6. 提交代码时文档更新与代码变更在同一个 commit 中

## 通用开发规范

- 默认语言：英文（UI、代码注释、错误信息、变量命名）
- 多语言支持：i18n 方案，翻译字典集中管理，默认 en
- 字体本地化：使用 @fontsource 等方案，不依赖外部 CDN
- 文档语言：中文（产品文档、设计文档面向团队内部）
- 导出文件默认保存到源文件同目录
- 敏感信息不硬编码（API Key、密钥等走配置文件或环境变量）

## CLAUDE.md 编写规范

项目级 CLAUDE.md 应包含：
1. 项目一句话描述
2. 项目结构（目录树 + 关键文件说明）
3. 开发命令（install / dev / build / test）
4. 关键设计决策（每条：决策内容 + 原因）
5. 数据存储位置（数据库、配置文件、缓存路径）
6. 命名约定（localStorage key 前缀、API 路径风格等）
