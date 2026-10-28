# librarian

外部资料只读研究 skill：查外部库、OSS、厂商 API 的官方文档与源码、版本差异、issue/PR 和变更历史，并把结论钉到 commit 与代码行，供主模型核验。

这是自包含分发单元：根目录 `SKILL.md` 是入口，`references/role.md` 是委派时逐字嵌入的行为正文。本地工作树调查不归它管，那是 explorer 的边界。

文档检索默认优先走 Context7（`https://mcp.context7.com/mcp`），依赖声明在 [agents/openai.yaml](agents/openai.yaml)。声明只是告诉宿主该 skill 期望什么能力，是否真的接通以子代理实际可见的工具为准；不可用时回退官方文档并说明限制。

## 安装

```bash
# 公开 skills 协议
npx skills add Kayphoon/librarian

# 本仓库自带安装器（零依赖，默认装到 ~/.agents/skills）
# 跟随最新的 1.x 发布：自动解析到匹配的最高 tag
npx github:Kayphoon/librarian#semver:^1.0.0
npx github:Kayphoon/librarian#semver:^1.0.0 --target codex
npx github:Kayphoon/librarian#semver:^1.0.0 --project ./my-repo
```

`#semver:^1.0.0` 每次都会解析到最新的 1.x tag，适合日常使用；想锁死具体版本就写 `#v1.0.3`，或者直接写 commit SHA。省略 ref 写 `npx github:Kayphoon/librarian` 则跟随默认分支 HEAD，可能包含还没发版的提交；替换已装副本加 `--force`。

装好后新开一次会话让运行时重新发现 skill。

## 许可与来源

本 skill 的行为文本是 [oh-my-openagent](https://github.com/code-yeongyu/oh-my-openagent) 中 MIT 许可 agent 提示词的改编版，不是上游原文件，也未获上游作者背书。上游署名与许可全文随本仓库分发：见 [NOTICE.md](NOTICE.md) 与 [LICENSE.txt](LICENSE.txt)。
