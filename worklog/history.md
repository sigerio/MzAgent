# 历史问题索引（archive）

- 标题：输入到输出全链路合理性团队审核
  路径：worklog/archive/技术实现/20260319-007-输入到输出全链路合理性团队审核.md
  摘要：已完成基于 `cunzhi` 问题的全链路审核，并实施 `respond_with_llm / expect_user_followup` 分支优先级修正，补入同轮 LLM 收口测试。

- 标题：cunzhi 结果未正常回流 LLM 收口
  路径：worklog/archive/技术实现/20260319-006-cunzhi结果未正常回流llm收口.md
  摘要：已改为在 `respond_with_llm = true` 时保留待续交互并继续同轮 LLM 收口，子仓版本提升至 0.1.35。

- 标题：用户消息发送后输入框未清空
  路径：worklog/archive/技术实现/20260319-005-用户消息发送后输入框未清空.md
  摘要：已改为发送后立即清空输入框，请求失败时回填原输入并恢复提交前历史与状态，子仓版本提升至 0.1.34。

- 标题：cunzhi 特化导致编排失真排查
  路径：worklog/archive/技术实现/20260318-010-cunzhi特化导致编排失真排查.md
  摘要：已移除 `cunzhi` 服务名硬编码触发，`auto` 改为统一由 LLM 路由，MCP 追问后的下一轮输入重新回流主链。

- 标题：添加模型后按钮布局 UI 评审
  路径：worklog/archive/技术实现/20260318-004-添加模型后按钮布局UI评审.md
  摘要：已完成设置抽屉按钮组间距微调与预览，当前按现有效果收口归档。

- 标题：移除 default 模型选项与空态隐藏
  路径：worklog/archive/技术实现/20260318-003-移除default模型选项与空态隐藏.md
  摘要：已移除前端内置 `default` 占位项，并在可用模型或启用模型为空时隐藏对应选择区块。

- 标题：cunzhi 调用失败 asyncio 事件循环冲突排查
  路径：worklog/archive/技术实现/20260318-009-cunzhi调用失败asyncio事件循环冲突排查.md
  摘要：已完成 MCP stdio 事件循环桥接修复，Web 场景下不再嵌套调用 `asyncio.run()`，真实 cunzhi 调用已验证恢复成功。

- 标题：Web 输入未触发 cunzhi MCP 调用排查
  路径：worklog/archive/技术实现/20260318-008-Web输入未触发cunzhiMCP调用排查.md
  摘要：已完成 auto 链式编排修复，显式 cunzhi 请求优先尝试 MCP，任一中间节点异常也不再阻断后续节点与最终 LLM 答复。

- 标题：Web 输入未与真实 LLM 交互排查
  路径：worklog/archive/技术实现/20260318-007-Web输入未与真实LLM交互排查.md
  摘要：已完成 auto 编排后的 LLM 强制收口修复，空 skills 可回退 LLM，真实 Web roundtrip 已验证最终返回 llm。

- 标题：输入框支持 Ctrl+Enter 发送
  路径：worklog/archive/技术实现/20260318-006-输入框支持Ctrl加Enter发送.md
  摘要：已完成 Web 输入框 Ctrl+Enter 快捷发送实现，保留普通 Enter 换行，并生成 Playwright 预览截图。

- 标题：LLM 真实 URL 测试失败与无法交互排查
  路径：worklog/archive/技术实现/20260318-005-LLM真实URL测试失败与无法交互排查.md
  摘要：已完成真实 LLM URL 修复，补齐默认 User-Agent 与 Responses 参数兼容性，真实联调与 CLI 交互均已恢复。

- 标题：NewAPI 多厂商模型切换方案讨论
  路径：worklog/archive/技术规划/20260318-008-NewAPI多厂商模型切换方案讨论.md
  摘要：已完成按模型协议保存与运行时分发改造，当前支持 `openai-responses`、`openai-completions`、`anthropic-messages` 三条链路。

- 标题：NewAPI 模型列表获取失败排查
  路径：worklog/archive/技术实现/20260318-002-NewAPI模型列表获取失败排查.md
  摘要：已完成 NewAPI 模型发现链路修复，真实环境下定位到 Cloudflare 1010 并通过补充 User-Agent 成功获取模型列表。

- 标题：LLM 连接配置存储与读取方案讨论
  路径：worklog/archive/技术规划/20260318-001-LLM连接配置存储与读取方案讨论.md
  摘要：已完成 LLM 配置仓收敛，取消 `.env` 参与链路并落地空仓显示“当前无配置方案”。

- 标题：LLM 免供应商配置方案讨论
  路径：worklog/archive/技术规划/20260318-002-LLM免供应商配置方案讨论.md
  摘要：已完成免供应商配置收敛，前端改为只围绕 NewAPI 连接与模型进行配置。

- 标题：NewAPI 反代协议选择讨论
  路径：worklog/archive/技术规划/20260318-003-NewAPI反代协议选择讨论.md
  摘要：已确认当前项目统一通过 NewAPI 的 OpenAI 风格入口访问模型，不再区分厂商原生协议。

- 标题：模型名称自动推断接口模式讨论
  路径：worklog/archive/技术规划/20260318-004-模型名称自动推断接口模式讨论.md
  摘要：已完成接口模式收敛，当前阶段不按模型名猜协议，内部固定使用 `responses` 调用链。

- 标题：NewAPI 多模型连接处理方案讨论
  路径：worklog/archive/技术规划/20260318-005-NewAPI多模型连接处理方案讨论.md
  摘要：已完成“单连接多模型”方案落地，内部改为统一连接配置配合多个可选模型条目。

- 标题：NewAPI 可用模型发现方案讨论
  路径：worklog/archive/技术规划/20260318-006-NewAPI可用模型发现方案讨论.md
  摘要：已完成模型发现能力接入，设置页支持从 NewAPI `GET /models` 拉取当前可用模型列表。

- 标题：NewAPI 网关与单模型启用方案讨论
  路径：worklog/archive/技术规划/20260318-007-NewAPI网关与单模型启用方案讨论.md
  摘要：已完成 NewAPI 网关配置、模型手动添加与单模型启用流程实现，子仓版本提升至 0.1.23。

- 标题：LLM 连接测试按钮
  路径：worklog/archive/技术实现/20260318-001-LLM连接测试按钮.md
  摘要：已完成当前选中配置方案的 LLM 连接测试按钮与后端探活接口接入，子仓版本提升至 0.1.22，并完成设置抽屉页面预览。

- 标题：全量 UI 重构
  路径：worklog/archive/技术实现/20260317-001-全量UI重构.md
  摘要：已完成 MzAgent Web 控制台 v0.1.21 前端增强，补齐 Markdown 渲染、消息操作按钮、能力字段映射与 SSE 快照接入，并生成 Playwright 预览截图。

- 标题：当前任务盘点
  路径：worklog/archive/任务管理/20260318-001-当前任务盘点.md
  摘要：已完成一次性任务盘点，确认唯一明确待办为 UI v0.1.21 前端增强，后续该任务已执行完成。

- 标题：后端接入任务清单与执行边界确认
  路径：worklog/archive/项目管理/20260317-002-后端接入任务清单与执行边界确认.md
  摘要：已完成后端接入收口，补齐 round 契约扩展、capabilities CRUD、指定轮次重试与 SSE 会话流，子仓版本提升至 0.1.20。

- 标题：CLI 改为 Web 端团队评审
  路径：worklog/archive/产品规划/20260314-002-CLI改为Web端团队评审.md
  摘要：已完成评审，确认 Web 端替代 CLI 主入口可行，保留 CLI 为调试入口，结论已落地到 Web 首版实现。

- 标题：Web 端实现方案团队评审
  路径：worklog/archive/产品规划/20260314-003-Web端实现方案团队评审.md
  摘要：已完成评审，收敛为轻量 ASGI JSON API + 单页薄界面方案，结论已落地并迭代至 v0.1.19。

- 标题：Web 端 UI 界面设计团队讨论
  路径：worklog/archive/产品规划/20260314-004-Web端UI界面设计团队讨论.md
  摘要：已完成首版 UI 信息结构讨论，后续用户选定 ChatGPT 风格布局替代原「单页任务控制台」方案。

- 标题：按 UI TODO 逐项实施 Web 端首版
  路径：worklog/archive/技术实现/20260314-005-按UI-TODO逐项实施Web端首版.md
  摘要：已完成 Web 首版实施（v0.1.9），包含共享服务层、最小 API、单页界面与门禁测试，后续由全量 UI 重构接管。

- 标题：当前活动任务确认
  路径：worklog/archive/项目管理/20260314-003-当前活动任务确认.md
  摘要：已完成一次性活动任务核对，结论已过期。

- 标题：Web 端 UI 任务编排
  路径：worklog/archive/项目管理/20260314-004-Web端UI任务编排.md
  摘要：已完成 7 Phase UI 任务编排，后续被全量 UI 重构方案替代。

- 标题：Web 端 UI TODO 清单梳理
  路径：worklog/archive/项目管理/20260314-005-Web端UI-TODO清单梳理.md
  摘要：已完成首版 TODO 清单梳理，后续被全量 UI 重构方案替代。

- 标题：NewAPI 版 UI 审查
  路径：worklog/archive/产品规划/20260316-009-NewAPI版UI审查.md
  摘要：已完成 NewAPI 风格控制台硬伤修复，删除重复表单与重复状态块，并通过宿主机 Playwright 生成新截图。

- 标题：参考 NewAPI 设计 Web 界面
  路径：worklog/archive/产品规划/20260316-008-参考NewAPI设计Web界面.md
  摘要：已完成一版参考 NewAPI 控制台分层思路的页面实现，并通过宿主机 Playwright 生成预览截图。

- 标题：开源 UI 设置与对话管理借鉴
  路径：worklog/archive/产品规划/20260316-007-开源UI设置与对话管理借鉴.md
  摘要：已完成开源 UI 在设置管理与对话管理上的借鉴分析，并回灌到首页结构回调实现。

- 标题：Git 搜索 Web 界面参考
  路径：worklog/archive/产品规划/20260316-006-Git搜索Web界面参考.md
  摘要：已完成 GitHub 开源 UI 参考调研，并将 AionUi、Vercel ai-chatbot、LobeChat 的优点用于本轮页面回调。

- 标题：Web 界面偏离参考设计复盘
  路径：worklog/archive/产品规划/20260316-005-Web界面偏离参考设计复盘.md
  摘要：已完成偏差复盘与页面结构回调，首页重新对齐为顶栏概览、主工作区、辅助状态区和折叠设置。

- 标题：Web 界面风格方案重选讨论
  路径：worklog/archive/产品规划/20260316-004-Web界面风格方案重选讨论.md
  摘要：已完成首页风格重选与实现，页面重构为清爽侧边栏布局，并通过宿主机 Playwright 生成预览截图。

- 标题：Web 界面二次重构与 Playwright 预览
  路径：worklog/archive/产品规划/20260316-003-Web界面二次重构与Playwright预览.md
  摘要：已完成首页二次重构，并通过宿主机 Playwright 生成整页预览截图。

- 标题：Playwright 预览与本地端口绑定受限排查
  路径：worklog/archive/技术实现/20260316-003-Playwright预览与本地端口绑定受限排查.md
  摘要：已补齐宿主机预览脚本，解决沙箱外 Web 启动与 Playwright 截图链路，生成稳定预览图。

- 标题：Web 界面重设计讨论
  路径：worklog/archive/产品规划/20260316-002-Web界面重设计讨论.md
  摘要：已完成 Web 首页重设计，首屏收敛为响应、提问与历史工作台，连接配置改为折叠式面板。

- 标题：Web 启动工具与使用入口缺失
  路径：worklog/archive/项目管理/20260316-002-Web启动工具与使用入口缺失.md
  摘要：已补齐 `start_web.sh`、示例环境模板与 README 最短使用路径，子仓版本提升至 0.1.11。

- 标题：保留原生 provider 并新增反代 profile 与页面切换讨论
  路径：worklog/archive/产品规划/20260316-001-保留原生provider并新增反代profile与页面切换讨论.md
  摘要：已完成原生 provider 保留、反代 profile 配置仓、页面切换方案与本轮实现收口，子仓版本提升至 0.1.10。

- 标题：LLM 接入扩展为 newapi 风格配置讨论
  路径：worklog/archive/技术规划/20260316-001-LLM接入扩展为newapi风格配置讨论.md
  摘要：已完成方案收敛，确认采用“保留原生 provider 驱动位 + 新增可切换反代 profile”的实现方向。

- 标题：按 todo 顺序执行后续修改
  路径：worklog/archive/项目管理/20260314-002-按todo顺序执行后续修改.md
  摘要：已按顺序完成 P1 与 C1~C5 收口，默认本地回归扩展至 69 项并全绿。

- 标题：制作详细任务清单
  路径：worklog/archive/项目管理/20260314-001-制作详细任务清单.md
  摘要：已完成当前阶段详细 todo 清单制定与 P0 收口执行，子仓已提交推送并待父仓联动收口。

- 标题：测试收口后所有 todo 项是否具备测试项与方法
  路径：worklog/archive/测试规划/20260314-003-测试收口后所有todo项是否具备测试项与方法.md
  摘要：已完成复核，确认当前实现面的所有 todo 已具备收口测试项与测试方法并验证默认回归全绿。

- 标题：根据 worklog 梳理需求并规划测试目录
  路径：worklog/archive/测试规划/20260312-001-根据worklog梳理需求并规划测试目录.md
  摘要：已完成测试目录收口，新增 runtime/perception/stm/knowledge/skills/integration 测试域并验证默认回归全绿。

- 标题：所有 todo 项是否已有收口测试项与测试方法
  路径：worklog/archive/测试规划/20260314-001-所有todo项是否已有收口测试项与测试方法.md
  摘要：已完成复核并完成当前实现面的测试收口，确认默认本地回归已覆盖九类测试域。

- 标题：按 todo 项设计测试用例与测试方案
  路径：worklog/archive/测试规划/20260314-002-按todo项设计测试用例与测试方案.md
  摘要：已完成按 todo 项的测试设计，并已回灌到真实测试目录、脚本与 README 说明。

- 标题：当前执行进度停点记录
  路径：worklog/archive/项目管理/20260311-007-当前执行进度停点记录.md
  摘要：已记录当前停点，确认真实 LLM、pyproject 驱动 MCP、最小 REPL 与首轮接口修复均已完成且未执行提交推送。

- 标题：团队审查上下游接口一致性
  路径：worklog/archive/项目管理/20260311-005-团队审查上下游接口一致性.md
  摘要：已完成团队审查并按结论修复 REPL 到 MCP/Tool 的参数桥接与 LLMRequest 字段透传缺口。

- 标题：REPL 中调用 cunzhi MCP 失败排查
  路径：worklog/archive/技术实现/20260311-004-REPL中调用cunzhiMCP失败排查.md
  摘要：已完成最小 REPL 的 cunzhi MCP 修复，支持 /mode、/target 与普通输入到 zhi.message 的桥接。

- 标题：CLI 对话窗形态可行性评估
  路径：worklog/archive/产品规划/20260311-001-CLI对话窗形态可行性评估.md
  摘要：已完成 `mz-agent` 最小 REPL 落地，支持持续输入、历史查看、重置与退出，并完成测试验证。

- 标题：真实 OpenAI 接口接入与后续路线实现评估
  路径：worklog/archive/技术实现/20260311-003-真实OpenAI接口接入与后续路线实现评估.md
  摘要：已完成真实 LLM provider、pyproject 驱动的 cunzhi MCP、文件持久化 STM 与 CLI 入口，并完成单测与联调验证。

- 标题：功能测试脚本与 README 团队讨论
  路径：worklog/archive/文档规划/20260311-004-功能测试脚本与README团队讨论.md
  摘要：已完成 README 重写、使用与测试脚本落地，并完成全量测试与演示脚本验证。

- 标题：按功能模块测试方式说明
  路径：worklog/archive/测试规划/20260311-003-按功能模块测试方式说明.md
  摘要：已完成按模块测试说明与脚本落地，并验证全量测试通过 `40 passed in 0.13s`。

- 标题：第一阶段全功能测试与实现范围收敛
  路径：worklog/archive/技术实现/20260311-002-第一阶段全功能测试与实现范围收敛.md
  摘要：已完成第一阶段全功能最小实现面与对应测试脚本落地，补齐运行时、主链编排和适配层。

- 标题：Python 版 Slice 1 首刀实现
  路径：worklog/archive/技术实现/20260311-001-Python版Slice1首刀实现.md
  摘要：已完成 `sub/MzAgentSub` 的 Python Slice 1 首批协议对象、状态门禁纯函数与契约测试骨架落地。

- 标题：当前是否可直接进行软件移植评估
  路径：worklog/archive/项目管理/20260311-006-当前是否可直接进行软件移植评估.md
  摘要：已完成团队评估，结论为不可直接全面移植，只可按 Python Slice 1 范围进入受控首刀实现。

- 标题：Python 版 Slice1 细化结论回灌讨论
  路径：worklog/archive/技术规划/20260311-009-Python版Slice1细化结论回灌讨论.md
  摘要：已完成动态字段矩阵、`transitions` 纯函数契约、跨对象一致性与 Guardrails 映射真值表收口，并正式回灌 `Slice 1` 主文档。

- 标题：Python 配置载体唯一方案收口讨论
  路径：worklog/archive/技术规划/20260311-008-Python配置载体唯一方案收口讨论.md
  摘要：已完成配置载体唯一方案收口，确认 Python 主线只保留 `pyproject.toml` 作为唯一标准入口。

- 标题：当前文档能否支撑软件实现团队评审
  路径：worklog/archive/项目管理/20260311-005-当前文档能否支撑软件实现团队评审.md
  摘要：已确认主文档回灌完成，当前文档集已足以支撑 Python Slice 1 首刀实现准备与受控开工。

- 标题：Python 配置文件载体调整讨论
  路径：worklog/archive/技术规划/20260311-007-Python配置文件载体调整讨论.md
  摘要：已确认 `mz.toml` 不能直接替代标准 Python 入口，配置载体议题暂停，不再阻塞 Python Slice 1 主线。

- 标题：Python 版 Slice 1 规划讨论
  路径：worklog/archive/技术规划/20260311-006-Python版Slice1规划讨论.md
  摘要：已完成 Python Slice 1 的对象边界、状态门禁、动态字段与 Guardrails 映射收口。

- 标题：sub 内第一阶段正式实现蓝图（Python 主线）
  路径：worklog/archive/技术规划/20260311-005-sub内第一阶段正式实现蓝图-Python主线.md
  摘要：已完成 Python 主线下的正式实现蓝图重画，明确目录边界、切片顺序与测试落点。

- 标题：第一阶段协议与门禁冻结总表
  路径：worklog/archive/技术规划/20260310-009-第一阶段协议与门禁冻结总表.md
  摘要：已完成第一阶段语言无关协议、状态机、权威边界与阻断级断言冻结，并作为 Python 主线依据保留。

- 标题：第一阶段实现就绪性复审
  路径：worklog/archive/项目管理/20260310-003-第一阶段实现就绪性复审.md
  摘要：已确认 Python 主线下第一阶段讨论已完成收敛，可进入文档收口与实现准备态。

- 标题：Python 主线规划文档重收敛
  路径：worklog/archive/项目管理/20260311-004-Python主线规划文档重收敛.md
  摘要：已完成从 Rust 主线到 Python 主线的 active 规划文档重收敛，并将 active 收口为三份核心文档。

- 标题：Python 技术栈切换重规划范围评估
  路径：worklog/archive/项目管理/20260311-003-Python技术栈切换重规划范围评估.md
  摘要：已完成切换到 Python 后需重规划范围的团队分析，并为文档重收敛提供依据。

- 标题：Rust 与 Python 实现便利性评估
  路径：worklog/archive/项目管理/20260311-002-Rust与Python实现便利性评估.md
  摘要：已完成 Rust 与 Python 在当前项目中的实现便利性对比，为后续主线切换提供前置判断。

- 标题：下一步讨论主题判断
  路径：worklog/archive/项目管理/20260311-001-下一步讨论主题判断.md
  摘要：已完成 Rust 主线下下一步讨论主题判断，其结论后续已被 Python 主线重收敛替代。

- 标题：sub 内第一阶段正式实现蓝图
  路径：worklog/archive/技术规划/20260310-010-sub内第一阶段正式实现蓝图.md
  摘要：已完成 Rust 主线版本的正式实现蓝图讨论，现作为切换到 Python 前的历史依据保留。

- 标题：active 归档与合并整理讨论
  路径：worklog/archive/项目管理/20260310-006-active归档与合并整理讨论.md
  摘要：已完成 active 清冗余与合并方案讨论，并据此将活跃结构压缩为三份核心文档。

- 标题：第一阶段最小代码契约清单讨论
  路径：worklog/archive/技术规划/20260310-004-第一阶段最小代码契约清单讨论.md
  摘要：已完成第一阶段最小代码契约清单首版冻结，并作为后续协议总表输入。

- 标题：第一阶段最小状态转移表讨论
  路径：worklog/archive/技术规划/20260310-005-第一阶段最小状态转移表讨论.md
  摘要：已完成 `step_state / cursor_state / react_status` 最小状态转移冻结，并作为后续门禁总表输入。

- 标题：第一阶段契约测试断言清单讨论
  路径：worklog/archive/技术规划/20260310-006-第一阶段契约测试断言清单讨论.md
  摘要：已完成第一阶段阻断级契约测试断言清单冻结，并并入协议与门禁总表。

- 标题：第一阶段唯一主实现路径讨论
  路径：worklog/archive/技术规划/20260310-007-第一阶段唯一主实现路径讨论.md
  摘要：已确认第一阶段唯一正式实现路径收敛为 `sub/MzAgentSub`。

- 标题：sub 内第一阶段落地蓝图讨论
  路径：worklog/archive/技术规划/20260310-008-sub内第一阶段落地蓝图讨论.md
  摘要：已完成子仓第一阶段落地蓝图讨论，并并入正式实现蓝图总表。

- 标题：当前阶段进展复核
  路径：worklog/archive/项目管理/20260310-001-当前阶段进展复核.md
  摘要：已完成当前阶段进度、未收口风险与推进状态复核。

- 标题：基于风险清单的当前讨论重点判断
  路径：worklog/archive/项目管理/20260310-002-基于风险清单的当前讨论重点判断.md
  摘要：已完成三处跨模块高优先级协议缺口的优先级判断。

- 标题：Phase 1 执行顺序与分流规则梳理
  路径：worklog/archive/项目管理/20260310-003-Phase1执行顺序与分流规则梳理.md
  摘要：已完成 Phase 1 执行顺序与动作分流规则梳理，其结论已被后续文档吸收。

- 标题：活跃文档归档候选判断
  路径：worklog/archive/项目管理/20260310-004-活跃文档归档候选判断.md
  摘要：已完成 active 文档归档候选判断，并作为本轮整理执行依据。

- 标题：当前工程进度检查
  路径：worklog/archive/项目管理/20260309-001-当前工程进度检查.md
  摘要：已完成当前仓库已讨论能力、工作区状态与后续推进优先级的初步盘点。

- 标题：src 框架对第一阶段设计支撑性评估
  路径：worklog/archive/项目管理/20260309-002-src框架对第一阶段设计支撑性评估.md
  摘要：已完成 `src/HelloAgents` 与 `src/agentscope` 对第一阶段设计的支撑性评估。

- 标题：全功能设计复审
  路径：worklog/archive/项目管理/20260309-003-全功能设计复审.md
  摘要：已完成第一阶段全功能设计复审，并识别三项后续已补齐的跨模块缺口。

- 标题：建立主仓库和子仓库映射关系
  路径：worklog/archive/仓库管理/20260302-001-建立主子仓映射.md
  摘要：已完成 sub/MzAgentSub 子模块拉取与 repos.md 主子仓映射建立。

- 标题：MzAgents 技术路径规划
  路径：worklog/archive/技术规划/20260302-001-MzAgents技术路径规划.md
  摘要：已完成 CLI + 自建 Core 路径及 Agent/Skill 边界等阶段性讨论。

- 标题：MzAgent 核心功能确认与技术路径补充（第一期）
  路径：worklog/archive/技术规划/20260304-001-MzAgent核心功能确认与技术路径补充.md
  摘要：已完成核心功能清单冻结、优先级分层及 P0 级 LLM 接入能力确认。

- 标题：MzAgent 功能职责划分与功能明确
  路径：worklog/archive/技术规划/20260304-002-MzAgent功能职责划分与功能明确.md
  摘要：已完成 10 项 P0 功能职责与接口边界 v1 逐项确认并冻结，未进入代码修改阶段。

- 标题：基于职责划分的功能实现细化讨论
  路径：worklog/archive/技术规划/20260305-001-基于职责划分的功能实现细化讨论.md
  摘要：已完成第一组模块（STM、LLM、Tool、MCP、Guardrails）M0 级实现细化与风险修补方案冻结。

- 标题：当前仓库进度与未收口状态同步
  路径：worklog/archive/项目管理/20260306-001-当前仓库进度与未收口状态同步.md
  摘要：已完成当前仓库历史进度、未收口变更与子模块异常线索的同步确认。

- 标题：LLM 接入层实现方案讨论
  路径：worklog/archive/技术规划/20260306-001-LLM接入层实现方案讨论.md
  摘要：已按第一阶段仅接入 OpenAI 的范围冻结 LLM 接入层统一协议、OpenAI adapter 与单 provider 路由。

- 标题：Tool 与 Function Calling 实现方案讨论
  路径：worklog/archive/技术规划/20260306-002-Tool与FunctionCalling实现方案讨论.md
  摘要：已按第一阶段 OpenAI function calling 范围冻结工具注册、执行请求、执行结果与单向调用链。

- 标题：MCP 接入层实现方案讨论
  路径：worklog/archive/技术规划/20260306-003-MCP接入层实现方案讨论.md
  摘要：已按“仅调用用户提供的 MCP”边界冻结第一阶段客户端接入、发现、调用与结果归一方案。

- 标题：Guardrails 实现方案讨论
  路径：worklog/archive/技术规划/20260306-004-Guardrails实现方案讨论.md
  摘要：已冻结 Guardrails 第一阶段职能、框架落点、规则范围及其对 Agent 的行为约束边界。

- 标题：Tool 与 Function Calling 功能边界复核
  路径：worklog/archive/技术规划/20260306-005-Tool与FunctionCalling功能边界复核.md
  摘要：已完成 Tool 与 Function Calling 第一阶段术语去歧义，确认冻结方案可继续沿用。


- 标题：核心功能剩余讨论项盘点
  路径：worklog/archive/技术规划/20260306-006-核心功能剩余讨论项盘点.md
  摘要：已完成 P0 核心功能已冻结项与剩余未冻结项盘点，并确认 Perception 为下一讨论优先级。


- 标题：Perception 实现方案讨论
  路径：worklog/archive/技术规划/20260306-007-Perception实现方案讨论.md
  摘要：已冻结 Perception 第一阶段职责边界、实现深度、输入输出、错误码及其与 STM 的交互边界。

- 标题：剩余核心功能依赖关系分析
  路径：worklog/archive/技术规划/20260306-009-剩余核心功能依赖关系分析.md
  摘要：已完成未冻结核心功能盘点，并收敛剩余模块间依赖关系与推荐讨论顺序。

- 标题：知识库实现方案讨论
  路径：worklog/archive/技术规划/20260306-010-知识库实现方案讨论.md
  摘要：已完成知识库第一阶段设计冻结，确认 KB M0 边界、最小数据模型、最小数据流与错误码范围。

- 标题：RAG 实现方案讨论
  路径：worklog/archive/技术规划/20260306-008-RAG实现方案讨论.md
  摘要：已完成 RAG 第一阶段设计冻结，确认 RAG M0 边界、固定预检索模式、输入输出边界、默认参数与错误码范围。

- 标题：Skills 第一阶段边界讨论
  路径：worklog/archive/技术规划/20260309-002-Skills第一阶段边界讨论.md
  摘要：已完成 Skills 第一阶段设计冻结，确认其仅作为用户 Skill 的接入与暴露层，并收敛最小输入输出、错误码与回退边界。

- 标题：Planning 第一阶段边界讨论
  路径：worklog/archive/技术规划/20260309-003-Planning第一阶段边界讨论.md
  摘要：已完成 Planning 第一阶段设计冻结，确认其仅作为步骤框架生成与约束表达层，并收敛最小输入输出、错误码与触发边界。

- 标题：Planning 后续功能讨论
  路径：worklog/archive/技术规划/20260309-005-Planning后续功能讨论.md
  摘要：已完成 Planning 后续路线第一版冻结，收敛显式重规划、计划诊断、版本回看与步骤产物语义四项增强方向。

- 标题：Skills / Planning / ReAct 依赖关系澄清
  路径：worklog/archive/技术规划/20260309-001-Skills-Planning-ReAct依赖关系澄清.md
  摘要：已完成 Skills、Planning、ReAct 的依赖顺序与职责关系澄清，并支撑后续三项独立冻结。

- 标题：ReAct 第一阶段边界讨论
  路径：worklog/archive/技术规划/20260309-004-ReAct第一阶段边界讨论.md
  摘要：已完成 ReAct 第一阶段设计冻结，确认其统一动作裁决与执行推进定位，并收敛最小协议、回退与终止边界。

- 标题：ReAct 与 Guardrails 固定挂点收口讨论
  路径：worklog/archive/技术规划/20260310-001-ReAct与Guardrails固定挂点收口讨论.md
  摘要：已完成 ReAct 与 Guardrails 第一阶段固定挂点顺序、动作/回答分流与通过条件收口。

- 标题：Planning 与 ReAct 的 current_step 来源收口讨论
  路径：worklog/archive/技术规划/20260310-002-Planning与ReAct的current_step来源收口讨论.md
  摘要：已完成 Planning、ReAct、STM 在 current_step 来源与运行态游标上的职责边界收口。

- 标题：关键主协议追踪标识落点收口讨论
  路径：worklog/archive/技术规划/20260310-003-关键主协议追踪标识落点收口讨论.md
  摘要：已完成 request_id、session_id、plan_id 在关键主协议中的统一落点、继承规则与生成边界收口。

- 标题：技术规划活跃文档归档可行性判断
  路径：worklog/archive/项目管理/20260310-005-技术规划活跃文档归档可行性判断.md
  摘要：已完成对 active/技术规划 下 3 份收口文档归档条件的判断，并确认其可归档。
