# codex-skills

跨电脑同步的 Codex 通用 skills 集合。

## 安装

将需要的 skill 文件夹复制到：

- Windows: `%USERPROFILE%\\.codex\\skills\\` 或 `%USERPROFILE%\\.agents\\skills\\`
- macOS/Linux: `~/.codex/skills/` 或 `~/.agents/skills/`

每个 skill 文件夹包含 `SKILL.md` 以及可能的 `scripts/`、`references/`、`assets/` 等资源。

`research-cycle` 与 `review-experiment` 共享实验协议和审查引用，请一起复制完整文件夹。前者负责有预算边界的实验规划与执行，后者负责因果、数据和功能证据审查。项目专用 profile 可保留在本机；公开仓库中的通用流程不依赖本机历史记录或可选执行器。

复制安装需要在每台电脑分别执行；仓库本身不建立自动持续同步。
