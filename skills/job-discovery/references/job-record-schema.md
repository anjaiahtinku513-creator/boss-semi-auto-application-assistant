# 岗位记录规范

## 单条岗位记录

每个岗位至少保留以下字段。未知值使用 `unknown`，不要猜测。

```yaml
job_key: "source job id or stable dedupe key"
source: "boss-visible-page | pasted-jd | public-web | export"
source_url: ""
captured_at: "ISO-8601 datetime with timezone"
title: ""
company: ""
recruiting_entity: ""
city: ""
district: ""
work_mode: "onsite | hybrid | remote | unknown"
salary:
  raw: ""
  min_monthly: null
  max_monthly: null
  months_per_year: null
experience_requirement: ""
education_requirement: ""
published_at: ""
recruiter_activity: ""
employment_type: ""
agency_or_outsourcing: "yes | no | unknown"
must_have_skills: []
preferred_skills: []
responsibilities: []
evidence_snippets: []
hard_gate:
  status: "pass | stretch | needs_review | hard_reject"
  reasons: []
score:
  provisional_score: null
  evidence_coverage: null
  tier: ""
  breakdown: {}
gaps: []
next_action: ""
```

## 去重顺序

1. 相同来源链接或职位 ID。
2. 标准化后的公司名、职位名和城市完全相同。
3. 上述字段相同且 JD 核心职责指纹高度相似。

保留信息最完整、采集时间最新的一条；把其他来源链接放入 `alternate_sources`，不要无痕删除。

## 候选表

默认表格列：

| 排名 | 公司 / 职位 | 薪资 / 地点 | 硬筛选 | 分数 | 证据覆盖率 | 主要匹配 | 主要缺口 | 建议 |
|---:|---|---|---|---:|---:|---|---|---|

表格后为每个推荐岗位附：

- 来源链接和采集时间。
- 3 条以内的强匹配证据。
- 3 条以内的主要风险或待确认项。
- 进入 `$resume-application-pack` 所需的完整 JD 和用户事实引用。

## 会话汇总

每轮搜索记录：

- `scanned_count`
- `deduplicated_count`
- `hard_rejected_count`
- `needs_review_count`
- `recommended_count`
- `stop_reason`
- 使用过的搜索词、城市和时间窗
- 用户批准进入下一阶段的 `job_key`
