# 项目博客写作 Skill

从真实的项目代码、实验日志和开发会话，整理出可复现、有个人判断的中文技术博客。

适合项目复盘、工具使用指南、排错记录和旧文改写。面向学生开发者的实践文章：写清问题、操作、取舍和验证，不编造指标或已经完成的工作。

## 文件

```text
skills/project-blog-writer/
├── SKILL.md
├── agents/openai.yaml
└── references/publishing.md
```

核心是写作流程指令；没有额外模型服务、收费接口或独立应用。`agents/openai.yaml` 提供显示名称与默认提示，发布参考按需读取。

## 在 Codex 中使用

克隆仓库，将 `skills/project-blog-writer` 整个目录复制到用户技能目录 `~/.codex/skills/`。Windows 默认对应 `%USERPROFILE%\.codex\skills\`。如果目录已存在，先比较内容，再决定是否更新。

Windows PowerShell 初次安装示例：

```powershell
git clone https://github.com/CyuYing/project-blog-writer.git
$taskSkillRoot = Join-Path $env:USERPROFILE '.codex\skills'
New-Item -ItemType Directory -Force -Path $taskSkillRoot | Out-Null
if (Test-Path (Join-Path $taskSkillRoot 'project-blog-writer')) {
    throw '技能目录已存在，请比较后更新，避免覆盖已有内容。'
}
Copy-Item -LiteralPath '.\project-blog-writer\skills\project-blog-writer' -Destination $taskSkillRoot -Recurse
```

重新打开或开始一个能识别该技能的 Codex 会话，然后明确调用：

```text
使用 $project-blog-writer，读取我指定的项目记录，
写一篇从数据准备到训练验证的中文实践博客。
保留有证据的数字，说明哪些步骤尚未完成，先交付草稿。
```

提供实际资料路径、会话或仓库，以及希望面向的读者。技能不会自己获得文件、网站或账号权限；读取和发布依赖当前会话中可用的工具。

## 输出与边界

- 用实际记录区分计划、已执行操作和历史实验快照。
- 数字写清日期、样本量与统计范围；效果提升需要评估证据。
- 标明项目自定义脚本，核实会变化的官方参数，保留来源链接。
- 移除密钥、密码和私人服务器信息，示例使用占位符。
- 用户要求发布时，沿用现有网站或仓库流程，并检查实际页面；没有发布请求时只交付文章。

建议检查三类任务：有日志的项目复盘、缺少量化证据的效果介绍、明确要求发布到现有 CMS 的文章。关注是否忠实于资料，而不是只看文章长度。

技能文件格式与本地目录用法参考 [OpenAI 技能实践说明](https://developers.openai.com/blog/eval-skills)。

## 许可

MIT。欢迎按自己的博客风格修改。
