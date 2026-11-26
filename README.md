# BOSS 半自动化简历投递 Agent

这是一个面向 BOSS 直聘等招聘场景的 Codex 插件。提供岗位筛选、简历定制、HR 回复起草和面试准备四项技能。用户负责审核材料，并在招聘平台上自行完成沟通和投递。

## 安装

在支持插件市场的 Codex CLI 中运行：

```sh
codex plugin marketplace add anjaiahtinku513-creator/boss-semi-auto-application-assistant
codex plugin add boss-semi-auto-application-assistant@boss-application-assistant
```

如果已经克隆本仓库，可以从仓库根目录运行 `codex plugin marketplace add .`，再运行上面的安装命令。安装后，在 Codex 中通过技能名称调用。

## 使用

| 技能 | 提供给 Codex | 生成的材料 |
| --- | --- | --- |
| [`$job-discovery`](skills/job-discovery/SKILL.md) | 岗位描述（JD）与真实履历、城市、薪资等条件 | 去重后的候选清单、硬筛选结果、匹配分数和证据缺口 |
| [`$resume-application-pack`](skills/resume-application-pack/SKILL.md) | 选定岗位的完整 JD、通用简历与可选的项目证据 | 定制简历草稿、打招呼话术、修改记录和事实核验 |
| [`$hr-chat-assist`](skills/hr-chat-assist/SKILL.md) | HR 的最新消息、必要岗位上下文和已确认的个人条件 | 可复制的回复草稿和需要用户确认的事项 |
| [`$interview-prep`](skills/interview-prep/SKILL.md) | 公司、完整 JD、简历和已确认的面试信息 | 附公开来源的公司研究、预测问题、回答要点和面试准备计划 |

最简单的用法是粘贴一份 JD 和与岗位相关的履历，输入：

> 用 `$job-discovery` 评估这份 JD，列出硬性条件、我能提供的匹配证据和仍需核实的信息。

选定岗位后，可用 `$resume-application-pack` 根据同一份 JD 和履历生成可审核草稿。收到 HR 回复或面试邀请后，再调用相应技能。

浏览器协作依赖当前 Codex 环境提供的浏览器能力，岗位筛选也可直接使用手动粘贴的 JD。面试准备中的公司研究需要联网检索公开资料。插件由技能说明和模板组成，无需为插件另配外部模型 API 密钥。

## 许可证

[MIT](LICENSE)
