# Go Backend Starter

AI 辅助 Go 后端开发 starter 模板。包含完整的约束体系、14 个专业 Skill、项目交付基线——为开发者与 AI 编码助手的结构化协作而设计。

## 特性

- **约束体系**：10 条编码约束，反例免疫格式（WRONG + CORRECT + Why）
- **专业 Skills**：14 个经过实战检验的工作流 Skill，覆盖完整开发生命周期
- **项目交付基线**：Docker、CI/CD、监控、运维手册模板开箱即用
- **知识进化闭环**：内置踩坑追踪和 Skill 进化机制

## 快速开始

1. 复制模板到新项目：
   ```bash
   cp -r go_backend_starter /path/to/your-project
   cd /path/to/your-project
   rm -rf .git && git init
   ```

2. 用 AI 助手开始编码——约束体系和 Skills 会自动引导工作流。

3. 根据项目需求定制 `CLAUDE.md`。

## 目录结构

```
.
├── CLAUDE.md                    # L1: 项目宪法（约束与规则）
├── README.md                    # 本文件
└── .claude/
    └── skills/                  # L4: 专业 Skills
        ├── brainstorming-with-context.md   # 设计阶段：代码探索 + 需求澄清 + 方案选择
        ├── plan-to-tasks.md                # 将设计拆解为 7 要素 Task
        ├── execute-with-review.md          # 7 步执行：读→实现→审查→构建→测试→提交
        ├── adversarial-review.md           # 多模型交叉验证代码审查
        ├── change-impact-scan.md           # Grep 驱动的变更影响扫描
        ├── competitive-analysis.md         # 功能设计前的竞品调研
        ├── false-positive-tracking.md      # 审查质量度量与规则调优
        ├── knowledge-loop.md               # PIT→规则→Skill→自动化→无感知 五级进化
        ├── pitfall-journal.md              # 踩坑记录与进化追踪
        ├── protocol-driven-development.md  # 参考文档优先的协议实现
        ├── test-strategy.md                # 测试金字塔 + 契约测试 + 混沌测试 + 快照测试
        ├── spec-checkpoint.md              # 7 阶段质量门禁
        ├── knowledge-snapshot.md           # 知识查阅优先级链
        └── project-delivery.md             # Docker、CI/CD、监控、运维手册模板
```

## 工作流

Skills 强制执行结构化的开发流程：

```
Brainstorming → Plan Tasks → Execute with Review → Adversarial Review（按需）
                    ↓                                    ↓
              Spec Checkpoints                    False Positive Tracking
              （7 阶段质量门禁）                    （审查质量度量）
```

### 新功能开发

1. **brainstorming-with-context** — 探索代码库，澄清需求，设计方案
2. **plan-to-tasks** — 将方案拆解为 Task（每个 Task 7 要素齐全）
3. **execute-with-review** — 读 → 实现 → Spec 审查 → 质量审查 → 构建 → 测试 → 提交
4. **change-impact-scan** — 每个 Task 完成后扫描改不全

### 代码审查

5. **adversarial-review** — 主模型 + 交叉模型审查，覆盖知识/注意力/确认偏差三大盲区
6. **false-positive-tracking** — 追踪 TP/FP 比率，调优审查规则

### 协议/API 开发

7. **protocol-driven-development** — 读参考文档 → 逐字段实现 → 交叉验证 → 6 类测试
8. **competitive-analysis** — 设计新 API 前调研竞品

### 知识管理

9. **pitfall-journal** — 记录每次犯错（PIT-xxx）
10. **knowledge-loop** — PIT → 规则 → Skill → 自动化 → 无感知（五级进化）

### 项目交付

11. **project-delivery** — Makefile、Dockerfile、CI/CD、监控、运维手册模板
12. **test-strategy** — 测试金字塔（70/20/10）+ 契约测试 + 混沌测试 + 快照测试

## 上下文层级

| 层级 | 位置 | 内容 | 加载时机 |
|------|------|------|----------|
| L1 项目宪法 | `CLAUDE.md` | 操作原则、编码约束、流程约束 | 每次会话 |
| L2 全局规则 | `~/.claude/rules/` | 不可变性、测试要求、性能策略 | 每次会话 |
| L3 领域知识 | `docs/` | 架构决策、API 契约、运行时机制 | 涉及对应模块时 |
| L4 专业 Skills | `.claude/skills/` | 工作流 Skills | 任务级匹配 |

## 编码约束摘要

| 编号 | 规则 | Why |
|------|------|-----|
| C-01 | 禁止吞错误 | 隐藏的错误会累积成线上事故 |
| C-02 | 禁止创建孤儿 context | 必须传递上游取消信号 |
| C-03 | 禁止对共享状态裸读写 | 并发 bug 难复现难定位 |
| C-04 | 每个 Open 必须配 Close | 资源泄漏随时间累积 OOM |
| C-05 | 所有外部输入必须校验 | OWASP Top 1 注入攻击 |
| C-06 | 魔法数字必须提取常量 | 3 个月后你不知道 60 是什么 |
| C-07 | 热路径只打 Warn/Error | 过多日志 I/O 成为性能瓶颈 |
| C-08 | 标准库 > 已有依赖 > 新依赖 | 最小化依赖面 |
| C-09 | 公共函数必须有测试 | 没有测试的代码无法安全修改 |
| C-10 | 协议实现必须对照参考文档 | 协议漂移是最危险的 bug |

## License

MIT

---

## 附录

### 一、核心理念层

1. Agentic Engineering vs Vibe Coding
- Vibe Coding = "prompt and pray"，靠运气出结果
- Agentic Engineering = 把 AI 当初级工程师管理，用结构化流程控制产出质量
- 关键转变：从"写好 prompt"到"设计好系统"

2. Harness Engineering 五层架构
- Layer 1: Context（上下文注入）—— 给 AI 足够的项目背景
- Layer 2: Constraints（约束系统）—— 用规则限制 AI 的自由发挥空间
- Layer 3: Feedback（反馈闭环）—— AI 犯错时记录并进化
- Layer 4: Automation（自动化管道）—— 可重复的执行流程
- Layer 5: Verification（验证机制）—— 多层检查确保质量
- 核心：不是让 AI 更聪明，而是让犯错成本更低、修复更快

3. 自动化成熟度三级跃迁
- L1：全手动，AI 辅助写代码，人工审查一切
- L2：人机协作，AI 自主完成已知模式，人工只审异常和新逻辑
- L3：全自动化，AI 自主完成端到端，人工只设规则和审结果
- 跃迁条件：L1→L2 需要约束体系和反馈闭环就绪；L2→L3 需要验证机制完善

4. Skill/Command/MCP 三层工具架构
- Skills = 业务逻辑层，封装完整工作流（如 brainstorming、code review）
- Commands = 路由层，薄壳，把用户输入转发给对应 Skill
- MCP = 外部服务集成层，连接数据库、API、文件系统等
- 好处：每层可独立迭代，Skill 可复用，Command 可组合

5. Superpowers 插件链式强制
- brainstorming → writing-plans → executing-plans 三阶段强制顺序
- 每阶段有明确产出和通过条件
- 不可跳过、不可并行、不可自主推进

### 二、上下文体系

6. 四层渐进上下文
- L1 项目宪法（CLAUDE.md）：操作原则、编码约束、流程约束——每次会话加载
- L2 全局规则（~/.claude/rules/）：不可变性、测试要求、性能策略——每次会话加载
- L3 项目领域知识（docs/）：架构决策、API 契约、运行时机制——涉及对应模块时加载
- L4 专业 Skill（.claude/skills/）：Go 审查、变更影响扫描、协议开发、踩坑进化——任务级匹配加载
- 加载规则：遇到不确定的细节，按 L3→L4 查找，禁止凭训练记忆编造

7. 上下文不是越多越好
- 过多上下文会稀释关键信息
- 按需加载，不是全量灌入
- 用 description 字段做精准匹配，让 AI 自动判断是否需要加载某个 Skill

### 三、约束系统

8. 反例免疫格式
- 每条约束三要素：WRONG 示例 + CORRECT 示例 + Why
- 不是告诉 AI"应该怎么做"，而是给边界："这是错误的，这是正确的，这是原因"
- AI 对具体代码示例的理解远优于自然语言描述

9. 流程阻塞约束
- 顺序不可跳过、不可并行：功能实现 → 单元测试 → 代码审查 → 提交
- 功能 Task 完成前，不得开始测试 Task
- 测试未通过前，不得标记功能 Task 完成
- 代码审查未通过前，不得提交 commit
- 只有用户明确要求跳过时才可跳过，且记录原因

10. 不确定性声明机制
- API/函数签名查证链走完仍无结果 → 明确告知用户
- Go 版本兼容性无法确认 → 明确告知
- 框架用法无法确认 → 明确告知
- 性能数据无实测支撑 → 不可断言
- 安全判断无法确认 → 明确告知
- 禁止行为清单：禁止编造函数签名、禁止编造标准库行为、禁止在无源码时声称已分析源码、禁止跳过实测直接推断、禁止编造 benchmark 数据

11. 改不全预防六条
- 调用点扫描：改了签名/接口 → Grep 所有调用点
- 正反操作配对：新增 Open/Create → 确认有 Close/Destroy
- 配置同步：改了配置项 → 检查 config struct、配置文件 example、docs
- 测试同步：改了实现逻辑 → 检查测试是否需要更新
- 文档同步：改了公共接口 → 检查 API 文档、README
- Migration 同步：改了数据模型 → 检查是否需要新增 migration
- 执行方式分级：单文件自主检查、多文件列影响范围、接口变更 Plan 模式

12. 文档生成约束
- AI 生成的文档/报告文件，单次任务不超过 5 个
- 超过 5 个先告知用户征得同意
- 每个文件生成后展示路径和大小
- 临时分析文件放 tmp/ 目录

### 四、自动化管道

13. Spec Checkpoint 七阶段门禁
- CP1 需求理解：理解摘要 + 假设列表，用户确认无误
- CP2 代码探索：模块清单 + 数据流 + 现有行为，涉及模块全覆盖
- CP3 方案设计：≥2 方案 + 推荐 + 变更清单，方案被选定
- CP4 Task 计划：Task 列表（7 要素齐全），计划被确认
- CP5 代码实现：spec review + quality review + build 通过，Critical/Major 清零
- CP6 测试通过：go test ./... 通过，测试全绿
- CP7 提交完成：commit message + MR 描述，用户确认
- 每个 CP：展示产出 → 等待用户确认 → 通过后才进入下一阶段
- 用户可说"通过/修改xxx/重来/跳过"（跳过仅限用户主动说）

14. Task 七要素规范
- 文件路径（精确到行号）
- 变更描述（改之前/改之后）
- 验证标准（可执行的命令或断言，不是"确认没问题"）
- 阻塞关系（前置任务、阻塞任务）
- 预估复杂度（简单≤10行/中等10-50行/复杂>50行）
- 关联指标（新增的 Prometheus metric 或无）
- 动词+名词标题格式

15. Execute-with-Review 七步执行流
- Step 1 Read：读目标文件及周边文件
- Step 2 Implement：写代码
- Step 3 Spec Review：对照 Task 描述检查实现是否完整
- Step 4 Quality Review：对照 CLAUDE.md 编码约束检查质量
- Step 5 Build：go build ./... 确认编译通过
- Step 6 Test：go test ./... 确认测试通过
- Step 7 Commit：原子 commit，message 包含变更说明
- 每个 Task 完成后执行 change-impact-scan

16. Brainstorming-with-Context 三阶段
- Phase 1 Code Explore：Grep 项目结构，找到相关模块、数据流、现有行为
- Phase 2 Requirements Clarification：和用户确认需求细节，列出假设清单
- Phase 3 Design Options：≥2 方案对比，推荐一个，附变更文件清单
- 必须先探索代码再出方案，禁止凭空设计

### 五、验证机制

17. 多模型对抗式 Code Review
- 触发条件：核心业务逻辑变更 / 变更文件≥5 / 变更行数≥200 / 用户要求
- 三个盲区理论：知识盲区（单个模型不知道）、注意力盲区（注意力分配不均）、确认偏差（自我验证通过）
- 五步流程：收集 diff → 主模型自审 → 调用独立审查 → 交叉验证 → 输出合并报告
- 交叉验证规则：两个模型都发现 → 高置信度；仅单模型发现 → 标注"需用户确认"
- 报告分级：Critical / Major / Minor / Suggestion

18. Change Impact Scan 四类变更
- 签名变更：改了函数签名/接口 → Grep 所有调用点
- 数据模型变更：改了 struct/db schema → Grep 所有序列化/查询点
- 配置变更：改了配置项 → 检查 config struct + YAML example + docs
- 路由变更：改了 HTTP 路由 → 检查前端调用 + API 文档 + 测试
- 输出影响报告：直接影响（必须改）/ 间接影响（建议改）/ 配置同步（检查项）

19. 协议驱动开发五阶段
- Phase 1 获取参考文档：读取协议规范原文，记录来源、字段数、必选/可选、枚举值、边界值
- Phase 2 逐字段实现：6 条反例免疫约束（不遗漏字段、不猜枚举值、不省略可选字段、不硬编码边界、不忽略错误码、不假设默认值）
- Phase 3 交叉验证：逐字段对照表，6 种漂移检测类型（遗漏、多余、类型不一致、枚举漂移、默认值漂移、命名不一致）
- Phase 4 测试文件：6 类测试（结构完整性、JSON RoundTrip、枚举值、缺失必选字段、未知字段、边界值），每类有完整 Go 代码模板
- Phase 5 兼容性声明：Breaking changes 列表 + 迁移路径 + 版本策略

20. 知识查阅优先级
- 项目 docs/ 目录 → 项目源码（Grep/Read）→ go.mod 依赖版本 → Context7 最新文档 → WebSearch 官方文档 → 全部走完 → 告知"不知道"
- 禁止未读 docs/ 就回答项目问题
- 禁止凭训练记忆断言框架行为
- 禁止未确认 Go 版本兼容性就用新版 API

### 六、反馈闭环

21. 踩坑进化闭环
- 触发条件：AI 生成错误代码被纠正 / 遗漏边界条件 / 使用不存在的 API / 改不全 / 不确定时编造信息
- PIT 记录格式：日期、类型（10种）、严重度、场景、现象、根因（5 Why）、修复、规则提炼、状态
- 10 种类型：改不全、幻觉、环境盲区、模式匹配代替验证、不会说不知道、并发、资源泄漏、错误处理缺失、协议漂移、review-false-positive
- 进化判断：1 次 → 仅记录；2+ 次 → 提炼为 CLAUDE.md 约束规则；规则验证 2+ 次 → 固化为独立 Skill；效果有限 → 标注"通用知识可覆盖"

22. Skill 分析与进化周期
- 两个独立维度评估：Recall Score（描述是否在正确场景触发）和 Effectiveness Score（内容是否产出好结果）
- Recall 评分：短语计数、动词多样性、生命周期覆盖、领域锚定、自然语言对齐
- Effectiveness 评分：工作流可执行性、渐进式披露、内容-触发对齐、内容完整性
- 进化周期：Scene Discovery → Diagnostic → User Discussion → Improve → Verify → Log
- 场景地图：Hit（正确触发）、Miss（应触发未触发）、False Positive（不应触发触发了）、Blind Spot（新场景未覆盖）
- 版本管理：语义化版本号，每次进化升级

### 七、项目交付体系

23. 项目结构基线
- 标准目录布局：cmd/、internal/、pkg/、configs/、docs/、scripts/、deploy/、.claude/skills/
- 每个目录有明确职责说明
- 临时文件统一放 tmp/

24. Makefile 规范
- 必须有目标：build、test、lint、clean、docker-build、docker-push、migrate-up、migrate-down、generate、help
- help 目标自动生成，显示所有可用目标
- 每个目标有 .PHONY 声明
- 变量覆盖机制（VERSION、DOCKER_REGISTRY 等）

25. 多阶段 Dockerfile
- Stage 1 Build：golang:1.22-alpine，编译静态二进制
- Stage 2 Runtime：alpine:latest，仅拷贝二进制 + 配置
- 非 root 用户运行
- HEALTHCHECK 指令
- 构建参数：VERSION、BUILD_TIME、COMMIT

26. Docker Compose 编排
- app + db + redis + nginx 四服务
- 健康检查配置
- 资源限制（deploy.resources.limits）
- named volumes 持久化
- .env 文件环境变量注入

27. CI/CD 管道
- ci.yml：PR 触发，含 lint + test + build + security scan
- release.yml：tag 触发，含 build + docker build + docker push + git tag + changelog
- 完整 GitHub Actions YAML 模板
- 缓存策略（Go module cache、Docker layer cache）

28. 配置与密钥管理
- 分层配置：default.yaml → environment.yaml → 环境变量
- 敏感信息只走环境变量或密钥管理服务
- .gitignore 包含 .env、.secret、configs/prod.yaml
- 配置 struct 与 YAML 一一对应，有反例免疫约束

29. 健康检查端点
- /health/live：存活探针，进程在就返回 200
- /health/ready：就绪探针，检查依赖服务（DB、Redis 等）
- /health/metrics：Prometheus metrics 暴露
- Kubernetes 探针配置模板

30. 监控告警
- RED 指标：Rate（请求速率）、Errors（错误率）、Duration（延迟分布）
- USE 指标：Utilization、Saturation、Errors（资源层面）
- 四个黄金信号：Latency、Traffic、Errors、Saturation
- Prometheus 告警规则模板（错误率超阈值、P99 延迟超阈值、CPU > 80%）
- Grafana Dashboard 建议

31. 日志规范
- 结构化日志（slog/zap），禁止 fmt.Println
- 日志级别：Debug（开发环境）/ Info（启动关闭）/ Warn（可恢复异常）/ Error（需人工介入）
- 热路径只打 Warn/Error（CLAUDE.md C-07 约束）
- requestID 关联全链路
- 日志轮转和归档策略

32. 数据库 Migration
- 线性版本号（001_init.sql、002_xxx.sql）
- 每个 migration 包含 UP 和 DOWN
- 不可修改已合入的 migration
- CI 中执行 migrate-up 验证
- 生产环境 migration 需要备份 + 回滚方案

33. 发布策略
- 语义化版本（SemVer）：MAJOR.MINOR.PATCH
- 发布检查清单：测试通过 → 版本号更新 → CHANGELOG 更新 → tag 创建 → CI 通过 → 部署 → 冒烟测试
- Canary 发布：先 5% 流量 → 观察 15 分钟 → 逐步扩大
- 蓝绿部署：两套环境切换，秒级回滚

34. 回滚方案
- 自动触发条件：错误率 > 5%、P99 > 3s、健康检查连续失败 3 次
- 回滚步骤：切流量到旧版本 → 验证旧版本健康 → 保留现场数据 → 事后分析
- 保留最近 N 个版本用于回滚

35. Runbook 运维手册
- 四类故障场景模板：服务不可用、数据库故障、第三方服务故障、性能劣化
- 每类场景：现象 → 排查步骤 → 修复方案 → 验证方法 → 事后动作
- 值班人员快速参考：关键命令、关键指标、关键联系人

### 八、Skill 设计方法论

36. Skill 的触发模式分类
- Reactive：用户明确请求时触发（如"review 代码"）
- Enforcement：在特定工作前强制触发（如"你必须在任何新功能前用这个"）
- Proactive：基于上下文自动触发（如检测到协议变更）
- 不同模式影响描述的写法和评估标准

37. Skill 描述的精确性
- 格式要求：Reactive 用"This skill should be used when…"；Enforcement 用"You MUST use this before…"
- 禁止寄生第二人称：描述中不能混入"you should"、"use this when you…"
- 不能模糊：不能用"provides guidance"、"helps with"等无具体信息的短语
- 不能冗余：描述不能只是重述 Skill 名称
- 必须有版本号

38. 触发短语工程
- 理想短语数 4-8 个，太少会漏触发（FN），太多会误触发（FP）
- 动词多样性：至少 2 个同义动词（如 create/add/set up/register）
- 生命周期覆盖：不仅覆盖创建，还要覆盖 debug/fix/check 阶段
- 场景触发：包含目标导向短语（如"X not working"、"how do I Y"）
- 领域锚定：包含至少一个领域专有名词或技术实体

39. Skill 内容的可执行性
- 每个工作流步骤必须评分 2/2：祈使动词 + 命名工具或命令 + 验证方式
- 评分 0 的示例："分析需求"、"理解架构"（太模糊）
- 评分 1 的示例："运行测试"（有动作但无具体命令和验证）
- 评分 2 的示例："运行 go test ./internal/service/...，检查输出是否全 PASS"

40. 渐进式披露
- 核心流程放 SKILL.md（<3000 字）
- 深度参考放 references/ 目录
- 示例代码放 examples/ 目录
- 脚本放 scripts/ 目录
- 每个 referenced 文件必须有"load when"条件（什么时候该去加载它）
- 禁止孤儿文件（存在但未被引用）、禁止断链（引用但不存在）

### 九、进阶实践

41. 竞品分析 Agent 团队
- 多角色子代理同时工作：一个做功能实现、一个做竞品分析、一个做测试
- 竞品分析 Agent 的价值：在实现新功能前，先用 WebSearch/DeepWiki 分析竞品的同类功能实现方式和设计决策
- 应用场景：设计 API 接口时参考行业标准、选择技术方案时参考业界最佳实践
- 落地方式：TeamCreate 创建多子代理，每个代理独立上下文，结果汇总后供用户决策
- 已落地为 competitive-analysis Skill

42. A/B 实验验证
- AI 提出的方案不应直接全量采纳，应设计 A/B 实验
- 实验要素：对照组（当前实现）、实验组（AI 方案）、评估指标、实验时长
- 应用场景：prompt 模板优化、缓存策略选择、超时参数调优
- 需要实验框架支持：feature flag + metrics 收集 + 统计显著性判断

43. 文档爆炸控制
- 已有约束：单次任务 AI 生成文档不超过 5 个
- 进阶：建立文档退休机制，定期清理过时文档
- 文档分级：活文档（代码同步更新）> 睡文档（定期审查）> 死文档（归档或删除）
- 自动检测：文档中引用的代码路径不存在时标记为过时

44. 误报追踪
- Code Review 中标注为 Critical/Major 的问题，需要记录是否为误报
- 误报率过高的规则需要调整或降级
- 真阳性/假阳性比率是衡量 Review Skill 质量的核心指标
- 已落地为 false-positive-tracking Skill
- PIT 类型已增加 review-false-positive

45. 团队能力退化风险
- 过度依赖 AI 可能导致工程师对底层技术的理解退化
- 防御策略：关键模块（安全、并发、性能）要求人工理解后才能合并
- AI 生成的代码必须经过人工审查，不能直接"看起来对就合"
- 定期手动 Review：每周选一个 AI 生成的模块，人工走读，确保团队理解

46. 渐进式上手路径
- 新成员不应一次面对全部 Skills 和约束
- 分阶段解锁：第一周只用基础 Skill（brainstorming + plan-to-tasks）；第二周加 execute-with-review；第三周加 adversarial-review 和 change-impact-scan
- 每阶段有验证点：能独立完成一个端到端任务
- 好处：避免认知过载，让每个 Skill 的价值被充分感受

47. 测试策略分层
- 已落地为 test-strategy Skill
- 测试金字塔——70% 单元测试 + 20% 集成测试 + 10% E2E
- 契约测试：上游/下游接口变更时，自动验证兼容性
- 混沌测试：随机注入故障（网络延迟、服务宕机），验证系统韧性
- 快照测试：协议响应结构变更时自动检测
- 覆盖率门禁：核心业务逻辑 >= 80%

48. Prompt 即代码
- CLAUDE.md 和 Skills 本质上是 prompt engineering 的工程化
- 它们应该和代码一样有版本管理、有测试、有 CI
- 改了 CLAUDE.md 的约束 → 应该验证 AI 行为是否如预期变化
- 落地方式：把典型场景做成 regression test，改约束后跑一遍确认行为正确

49. AI 行为的可观测性
- 记录 AI 每次操作的决策过程：为什么这样改、考虑了什么、拒绝了什么
- 用 structured logging 记录 AI 行为（不是给用户看的，是给自己复盘的）
- 定期分析 AI 的错误模式，看是否有系统性偏差
- 落地方式：PIT 记录就是第一步，后续可以做成 dashboard

50. 知识管理闭环
- 从代码中来：每次踩坑都记录 PIT
- 到约束中去：PIT 重复 2+ 次提炼为规则
- 从规则到 Skill：规则验证 2+ 次固化为 Skill
- 从 Skill 到自动化：成熟的 Skill 可以做成命令或 MCP 工具
- 从自动化到无感知：最终目标是开发者不需要知道这些规则的存在，系统自动执行
- 已落地为 knowledge-loop Skill

### 十、思维模型

51. AI 是初级工程师
- 需要明确的任务描述（Task 7 要素）
- 需要明确的约束（反例免疫格式）
- 需要明确的检查点（Spec Checkpoint）
- 需要明确的反馈（踩坑进化闭环）
- 不能假设它"应该知道"

52. 约束 > 提示
- 一条具体的约束（"禁止吞错误"）远优于一段描述性的期望（"请处理好错误"）
- 约束是可以验证的，期望是主观的
- 约束可以被自动化检查（如 lint 规则），期望不行

53. 犯错是资源
- 每次犯错都是在告诉你系统哪里有漏洞
- 记录、分类、分析、修复、预防——五步闭环
- 错误的模式比单个错误更重要
- 系统性地消除错误模式，比逐个修复更高效

54. 系统思维 > 点状优化
- 不是"写好 prompt"，而是"设计好系统"
- 上下文体系、约束系统、自动化管道、验证机制、反馈闭环——五者缺一不可
- 优化单个环节的效果有限，五者协同才能产生质变
- 衡量指标：从需求到上线的全链路时间、返工率、bug 逃逸率
