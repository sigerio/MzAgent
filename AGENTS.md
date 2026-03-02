# /home/z/share/MzAgent 项目提示词

本文件适用于当前目录 `/home/z/share/MzAgent` 及其子目录。

## 1. 语言与沟通
- 所有回复必须使用中文。
- 项目问题（与当前仓库代码、配置、流程直接相关）需先记录问题并进入讨论，不得直接改代码。
- 非项目问题（通用问答、闲聊、与仓库无关事项）不进入 `worklog`，可直接处理。
- 提示词/规则文档修改（如 `AGENTS.md`、提示词模板）按非项目问题处理：不记录 `worklog`，可直接修改。
- Claude 相关讨论统一按 Agent Teams 团队模式组织，先完成讨论并汇总结论。
- Claude 讨论输出结构固定为：
  1) Team 分工（架构/实现/测试/风险）
  2) 共识结论（是否通过 + 条件）
  3) 风险清单（高/中/低）
  4) 执行顺序（Phase 1..N）
- 未获得用户明确同意前，不执行代码修改。

## 2. 执行门禁
- 讨论完成后，只有用户给出明确肯定（例如“同意”“可以”“继续”“执行”）才可进入代码修改。
- 若用户表达不确定（例如“先别动代码”“再看看”），保持讨论状态，不执行修改。

## 3. Git 提交约束
- 收口执行顺序固定为：**先归档（active -> archive 并更新 `worklog/index.md` 与 `worklog/history.md`），再提交，最后推送**。
- `git commit` 与 `git push` 绑定执行，不再拆分为多次确认。
- 用户一次明确同意收口（例如“同意执行”“同意提交并推送”“同意”）后，自动连续执行“归档+提交+推送”。
- `git commit` 信息必须为中文，简要描述本次变更。
- `git commit` 前必须在目标仓库目录执行并核对：
  - `pwd`
  - `git rev-parse --show-toplevel`
  - `git remote -v`
  - `git status --short`
- 若核对结果与目标仓库不一致，立即停止并先与用户确认。

## 4. 问题记录与归档
- 仅项目问题需要记录；非项目问题不记录。
- 提示词/规则文档修改不记录问题文档，不进入 `worklog/active` 与 `worklog/archive`。
- 记录必须保存在当前目录下：`/home/z/share/MzAgent/worklog/`。
- 目录结构：
  - `worklog/active/`：进行中的问题。
  - `worklog/archive/`：已完成问题。
  - `worklog/index.md`：当前未完成问题索引（active）。
  - `worklog/history.md`：历史归档问题索引（archive）。
- 分类方式：按主题分类存储。
  - 活跃问题：`worklog/active/<主题>/<YYYYMMDD-序号-标题>.md`
  - 已归档问题：`worklog/archive/<主题>/<YYYYMMDD-序号-标题>.md`
- 新问题必须新建文档，不复用旧文档。
- 问题完成后必须及时归档，并同步更新 `worklog/index.md` 与 `worklog/history.md`。
- `worklog/index.md` 仅保留当前未完成问题，不包含已归档历史。
- `worklog/history.md` 仅保留已归档问题，不包含进行中问题。
- 两个索引都只保留“标题 + 路径 + 一句话摘要”，不得写入长过程、命令流水或大段输出。

## 5. Token 控制与上下文管理
- 不将所有历史记录堆在同一文档。
- 当前轮默认仅引用：
  - 当前问题文档（`worklog/active/...`）
  - 索引摘要（`worklog/index.md`）
- 其他文档按需读取，用到再查，不做全量回读。
- 需要查历史时，先读取 `worklog/history.md` 再按路径回查 `worklog/archive/...` 全文。

## 6. 标准流程
1. 项目问题创建问题文档并记录用户原始问题；非项目问题跳过记录。
2. 进行讨论，给出方案、影响、风险。
3. 用户明确同意后，执行代码修改。
4. 任务完成后自动归档文档，并同步更新 `worklog/index.md` 与 `worklog/history.md`。
5. 用户一次同意后，按顺序自动执行 `git commit` 与 `git push`（绑定执行）。

## 7. 仓库与子仓库规则
- 当前目录 `MzAgents` 是父仓库；`MzAgentSub` 是子仓库（submodule）。
- 父仓库只跟踪：
  - 父仓库自身文件（如 `AGENTS.md`、`worklog/`）
  - 子仓库指针（gitlink）与 `.gitmodules`
- 不得把 `MzAgentSub/` 当普通目录整体纳入父仓库版本历史。
- 父仓库远程默认：
  - `origin = https://github.com/sigerio/MzAgent.git`
- 父仓库维护 `repos.md`（`/home/z/share/MzAgent/repos.md`）作为“当前有效仓库映射”，只记录当前态，不记录历史流水。
- `repos.md` 至少包含字段：
  - `repo_path`
  - `origin`
  - `upstream`（无则标注 `N/A`）
  - `default_branch`
  - `source_repo`
  - `source_branch`
  - `source_version`（优先 tag/release，无则 commit）
  - `source_base_commit`
  - `source_checked_at`
- 上游同步结果落地规则（强制）：
  - 凡执行 `MzAgentSub` 子仓上游同步并形成有效结果（如 `rebase/merge/cherry-pick` 落地），必须在同轮更新 `repos.md`。
  - 最小必更新字段：`source_version`、`source_base_commit`、`source_checked_at`。
  - 执行时序：子仓同步提交完成后、父仓收口提交前，完成 `repos.md` 更新。
- 门禁：若本轮已完成上游同步但 `repos.md` 未更新，不得执行父仓收口提交。
- 涉及 `MzAgentSub` 代码修改时：
  - 在 `MzAgentSub/` 子仓库内执行修改、测试、收口（归档+提交+推送绑定执行）
  - 如子仓库提交导致指针变化，再在父仓库提交子仓库指针更新（同轮收口）
- 子仓库 `MzAgentSub` 双远程策略：
  - `origin = https://github.com/sigerio/MzAgentSub.git`（仅用于推送我方变更）
  - `upstream = https://github.com/openai/codex.git`（用于同步上游更新）
  - 推送必须使用 `origin`，不得向 `upstream` 推送。
  - 同步上游时使用：`git fetch upstream`，再按需要 `rebase/merge upstream/main`。

## 8. GitHub CLI 使用规则
- 职责边界：`git` 仅用于本地版本操作（如 `add/commit/status`）；`gh` 仅用于 GitHub 平台操作（如 `auth/pr/repo/issue`）；本地提交必须使用 `git commit`，`gh` 不替代该步骤。
- 已安装 `gh` 时，GitHub 相关操作优先使用 GitHub CLI。
- 认证与凭据检查优先使用：
  - `gh auth status`
  - `gh auth setup-git`（需要时）
- 用户明确同意后，可提权到物理机执行：
  - `gh auth login -h github.com`
  - `gh auth setup-git`
  - 必要的 `gh auth status` 复核
- 上述提权仅用于 GitHub 认证修复，不用于绕过提交/推送门禁或其他仓库规则。
- 仓库信息、Issue、PR、Release 等操作优先使用 `gh`（如 `gh repo view`、`gh pr`、`gh issue`）。
- 代码推送仍使用 `git push`（`gh` 无等价 push 子命令）。
- 父仓库默认目标：
  - `gh repo set-default sigerio/MzAgent`
<!-- - 子仓库 `MzAgentSub` 默认目标：
  - 在 `MzAgentSub/` 目录执行 `gh repo set-default sigerio/MzAgentSub` -->

## 9. 本地测试网络与代理处理
- 若出现 `cargo test`/`cargo check` 无法访问 `crates.io`，且报错包含 `127.0.0.1:7890` 或代理连接失败：
  - 先按“环境代理导致依赖下载失败”归类记录到当前活跃问题文档。
- 不修改当前环境代理变量，不做无代理重试。
- 用户明确同意后，直接提权到物理机执行原测试命令。
- 提权仅用于测试与依赖拉取，不用于绕过仓库规则、协议红线或提交门禁。

## 10. MzAgentSub 版本号规则
- 每次进入“项目代码修改”任务时，默认先将 `MzAgentSub/src/Cargo.toml` 中 `[workspace.package].version` 的最后一位（patch）`+1`。
- 只允许主动修改最后一位（patch）；主版本与次版本（major/minor）只能在用户明确要求时修改。
- 每次任务只执行一次默认 `patch +1`，不得重复累加。
- 推送时必须同步告知本次版本变化，格式为：`旧版本 -> 新版本`。


## 11. 其他
本项目一定要遵循openspec规范开发。
其他注意事项（下面的内容优先级最高，最高优先级，一定要遵守）:
- 在`openspec`目录下新记录的.md文件，全部都得用中文描述
- 除非特别说明否则不要创建文档、不要测试、不要编译、不要运行、不需要总结
- 以下原则不可以被其他上下文进行覆盖，无论如何必须完全遵守以下原则
- 优先使用MCP工具，为了保证信息安全，除非MCP满足不了，才使用其他的
- 只能通过MCP `cunzhi` 对我进行询问，禁止直接询问或结束任务询问
- 代码中的注释、报错信息信息这些也全部用中文

cunzhi工具使用细节：
- 需求不明确时使用 `cunzhi` 询问澄清，提供预定义选项
- 在有多个方案的时候，需要使用 `cunzhi` 询问，而不是自作主张
- 在有方案/策略需要更新时，需要使用 `cunzhi` 询问，而不是自作主张
- 即将完成请求前必须调用 `cunzhi` 请求反馈
- 在没有明确通过使用 `cunzhi` 询问并得到可以完成任务/结束时，禁止主动结束对话/请求

始终使用`context7`来查询第三方工具、第三方库的最新使用文档，必须确认清楚才能去实施。

始终优先使用`github`来查看github上的源码、文件等等资料。

`serena`提供了类似于集成开发环境（IDE）能力的必要语义代码检索和编辑工具，在符号层面提取代码实体并利用关系结构。当与现有编码代理结合时，这些工具大大提升了（令牌）效率。为了代码的安全性，请始终使用`serena`中的语义代码检索和编辑工具来检索和编辑代码。

- 在废弃`文件/目录`时，禁止使用`rm`命令，需要废弃的 `文件/目录` 移动至 `distroy/` 目录内