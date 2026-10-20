# SAVAGE 页面设计工具选型

日期：2026-10-15。依据：SAVAGE-PRD-v4.1.md。范围：GitHub 官方仓库的能力、接入方式与本项目适配评估；未安装候选工具，未做同题生成实测。

## 1. 选型结论

建议以 **UI UX Pro Max 提供设计规范参考，Impeccable 负责原型后的审查与打磨**。如果只新增一个设计技能，优先试 UI UX Pro Max：本项目最终面向 iOS/Android，它的资料包含 SwiftUI 和 Jetpack Compose 指引。这个推荐是项目适配判断，不是生成质量排行榜。

当前已具备 Frontend App Builder、Imagegen 和浏览器验证能力，足以开始视觉概念与后续网页交互原型。无需等所有候选安装完再设计。

Figma 是需要可编辑设计稿时的交付工具。当前目录中可用的 Figma 插件需安装并连接后才能实际操作。GitHub 的 Talk to Figma MCP 是可选替代桥接方案，不建议同时维护多套 Figma 写入链路。

## 2. 六个候选的对比

“成本”指相对接入与维护成本，不是订阅报价；开源许可也不代表模型、Figma 或托管服务免费。

| 工具 / 官方仓库 | 类型与能力 | 对 SAVAGE 的价值 | 局限与接入成本 | 建议 |
|---|---|---|---|---|
| [UI UX Pro Max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) | AI 设计技能；检索配色、字体、UX 与平台指引，生成设计系统建议；MIT | 将 PRD 转成一致的色彩、字号、间距与移动端规则；包含 SwiftUI/Compose 资料 | 搜索脚本需要 Python；建议不等于成品；缺少产品约束时可能套入泛化模板。成本低到中 | **优先试用，负责规范** |
| [Impeccable](https://github.com/pbakaus/impeccable) | AI 设计技能及工具；提供 critique、audit、polish、harden 等审查和改进流程；Apache-2.0 | 检查页面层级、拥挤、错误态、文本溢出与视觉一致性 | 主要围绕前端；完整安装可涉及引擎和 hooks，需区分技能与运行工具。通用审美规则不能覆盖 PRD。成本中 | **原型阶段优先，负责打磨** |
| [Anthropic frontend-design](https://github.com/anthropics/skills/tree/main/skills/frontend-design) | 精简的前端设计技能；强调明确风格和非模板化实现；该技能目录为 Apache-2.0 | 适合小范围视觉探索，接入简单 | 不是完整设计系统数据库，也不是画布工具；与现有 builder 和 Impeccable 指导重叠。成本低 | 作为备选，不叠加多个主设计指令 |
| [Talk to Figma MCP](https://github.com/grab/cursor-talk-to-figma-mcp) | MCP + Figma 插件；支持创建和修改 Frame、文本、Auto Layout、组件实例；MIT | 能输出可编辑 Figma 元素，方便设计师继续修改 | 需要 Bun、MCP、WebSocket 和 Figma 插件配合；Windows/WSL 有额外连接配置。它负责操作画布，不能保证审美。成本较高 | 确定走 Figma 自建链路时再用 |
| [Framelink / Figma Context MCP](https://github.com/GLips/Figma-Context-MCP) | 提供 Figma 设计数据给编码助手；MIT | 已有完整设计稿后，帮助还原布局和样式 | 核心是读取设计上下文，不应视为从零绘制页面的工具；需要 Figma 凭据及 MCP 配置。成本中 | 设计转代码阶段再评估 |
| [shadcn/ui](https://github.com/shadcn-ui/ui) | 可修改源码的 Web UI 组件体系；MIT | 快速搭建可点击网页原型中的对话框、开关、分段选择等 | 是 Web 组件而非原生 App 设计插件；默认外观需要重做，不能直接替代 SwiftUI/Compose。成本中 | 网页原型按需使用基础组件 |

仓库地址注意：原 sonnylazuardi/cursor-talk-to-figma-mcp 地址当前重定向到 grab/cursor-talk-to-figma-mcp。

## 3. 为什么不直接选“星标最多”的一个

- 技能决定生成与审查方法；MCP 决定能读写哪些设计资源；组件库决定交互实现基础。三者不互相替代。
- GitHub README 和演示只能证明公开描述了相应能力。本次没有测出页面质量胜率、节约时间或 Windows 安装成功率。
- 已检查官方仓库与文档；未取得可靠的最近提交日期，不据此宣称任何项目持续活跃或长期维护有保障。安装前再核对 release、近期 issues、版本和依赖。
- 采用第三方工具时固定版本，保留许可，不直接复制整包配置覆盖已有技能。Figma Token 不写入仓库；桥接服务默认仅限本地。
- Impeccable 的通用反模板规则不能导致本项目丢掉深紫品牌色、近黑专注页或平台适配字体。明确产品需求优先。

## 4. 建议工作顺序

1. 以 PRD 定义页面与异常状态，建立一份统一设计规范。
2. 生成核心视觉概念，审查角色、文字、对比度和页面密度。本次已完成首版六屏概念。
3. 制作移动端可点击原型，先验证“邀请 → 准备 → 专注 → 恢复/完成 → 战报”的操作理解。
4. 在真实渲染页面上做审查；如引入 Impeccable，此阶段使用，而不是同时运行多套生成流程。
5. 需要设计师协作时输出 Figma 图层与组件；需要原生开发时输出 token、状态表、资产和规格。

网页原型只验证页面与交互，不验证后台运行、传感器精度、两机同步或商店审核。正式 App 的原生能力仍按 PRD 单独验证。

## 5. 同题试用验收

如下一步安装候选，用相同 PRD、相同输入、相同页面（首页、恢复、异常结果）比较，不用各项目官网演示互相比较。

| 维度 | 权重建议 | 验收方式 |
|---|---:|---|
| 产品规则正确 | 30% | Solo 可见；挑战默认关；系统异常不判用户失败 |
| 移动端可用性 | 25% | 小屏、长昵称、大字体、触控区、对比度逐项检查 |
| 视觉辨识与一致性 | 20% | 六屏统一，首页有个性，专注页安静 |
| 可编辑与实现成本 | 15% | 组件/token 可复用；设计到实现无大幅返工 |
| 安装与维护成本 | 10% | Windows 运行、依赖、凭据、更新可控 |

权重是本项目建议；尚无实测分数。违反核心产品规则的方案先修正，不用视觉得分抵消。

## 6. 本轮产物与状态

- 页面规格：[SAVAGE-Page-Design-v0.1.md](SAVAGE-Page-Design-v0.1.md)。
- 六屏视觉概念：`../design/concepts/savage-core-screens-v1.png`。
- 使用现有内置 Imagegen 生成概念。没有将候选工具的能力描述当成已安装或已运行结果。
- 图稿为首轮视觉探索，不是可点击原型、可编辑 Figma 文件或原生 App。

## 7. 核对依据

- [UI UX Pro Max README](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill#readme)：能力、平台、Python 前提。
- [Impeccable README](https://github.com/pbakaus/impeccable#readme)：命令、安装方式与许可。
- [frontend-design 技能](https://github.com/anthropics/skills/blob/main/skills/frontend-design/SKILL.md) 与 [该目录许可](https://github.com/anthropics/skills/blob/main/skills/frontend-design/LICENSE.txt)。
- [Talk to Figma README](https://github.com/grab/cursor-talk-to-figma-mcp#readme)：读写工具、Bun/WebSocket、Windows 配置。
- [Framelink README](https://github.com/GLips/Figma-Context-MCP#readme)：设计数据读取与编码用途。
- [shadcn/ui README](https://github.com/shadcn-ui/ui#readme)：组件源码与许可。
