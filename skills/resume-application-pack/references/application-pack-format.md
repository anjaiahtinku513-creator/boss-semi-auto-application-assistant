# 申请材料包格式

下列结构用于完整材料包。局部简历/话术修改沿用已有岗位上下文，按用户要求交付对应正文及必要的事实核验；不为填模板新建无关文件或栏目。各岗位的来源、事实、版本和审批状态分别保存。

## 对话交付

用户未要求保存文件时，直接在对话中按以下顺序交付：

1. `材料状态`
2. `关键匹配与主要缺口`
3. `待确认事实`
4. `定制简历草稿`
5. `打招呼话术`
6. `修改日志`
7. `事实核验`

## 文件交付

仅在用户明确要求保存或导出时创建独立目录：

```text
output/job-applications/YYYY-MM-DD/<company>__<role>__<job-key>/
  source-jd.md
  tailored-resume.md
  greeting.md
  change-log.md
  truth-check.md
  manifest.yaml
```

文件名使用安全字符；若公司或职位含非法字符，做最小替换并在 `manifest.yaml` 保留原名。主简历不得放在此目录中被覆盖。

## 修改日志

```markdown
| ID | 模块 | 修改前 | 修改后 | 对应 JD | 事实来源 | 操作类型 | 原因 |
|---|---|---|---|---|---|---|---|
```

操作类型限定为：`reorder`、`compress`、`clarify`、`keyword-align`、`remove`。若需要使用其他类型，先说明为什么不会改变事实。

## 事实核验

```markdown
| 声明 | 状态 | 来源 | 核验说明 | 是否进入草稿 |
|---|---|---|---|---|
```

任何没有来源的新增声明都必须为 `pending_confirmation` 且“是否进入草稿”为“否”。

## Manifest

```yaml
job_key: ""
company: ""
role: ""
source_url: ""
created_at: "ISO-8601 datetime with timezone"
master_resume_source: "path or conversation"
facts_source: "path or conversation"
status: "blocked | ready_for_user_review | user_approved"
pending_confirmations: []
files: []
```

没有用户对当前版本的明确批准，不得写 `user_approved`。批准后若正文再次变化，状态自动退回 `ready_for_user_review`。
