# Skill 对比验证：PR 审查

> **实验设置**：同一 LLM（DeepSeek-v4-Flash）× 同一 PR（pi-mono [#6632](https://github.com/earendil-works/pi/pull/6632）：fix RPC extension results）× 不同 skill prompt。
>
> 对照组：pi 原生 `pr.md`
> 实验组：pi 原生 `pr.md` → PEVM 结构化卡片 → 格式转换 → `skill.pi.md`

## 原生 pi pr.md 输出节选

```
PR: https://github.com/earendil-works/pi/pull/6632

### What it does
This PR fixes RPC extension output and error correlation: extension command
stdout is now emitted as a protocol-safe 'extension_output' event...

### Good
- The core mechanism is clean and correctly correlates concurrent RPC commands
- Backward compatibility is respected: onEvent still only receives agent events
- The assertSuccess helper makes void-method rejection explicit
- promptAndWait was improved to handle preflight failures and timeouts

### Bad
- No README/docs were updated despite public RPC protocol changes
- RpcExtensionError.requestId is set for all errors, not just command errors

### Ugly
- Manual mock of withStdoutRedirectHandler duplicates production logic
- assertSuccess type-narrowing relies on Extract but still casts

### Tests
- Excellent coverage, 1545 tests passed
- Gap: no test for concurrent RPC prompts with overlapping extension calls
```

## PEVM skill.pi.md 输出节选

```
**PR URL**: https://github.com/earendil-works/pi/pull/6632

**Processing Flow**
- 获取PR URL后，添加 inprogress 标签表示开始审查
- 读取PR全貌：提取标题、描述、关联issue、变更文件列表
- 分析 diff：对比 main 分支的变更内容
- 检查关联 issue：验证 issue 状态与 PR 目标是否一致
- 将 inprogress 标签替换为 reviewed 标签

**Input Requirements**
- PR URL 必须可访问且指向 GitHub 托管项目
- 项目存在 main 分支作为比较基线

**Output Format**
- PR URL → What it does / Good / Bad / Ugly / Tests / Open questions
- 每段必须包含至少一条具体证据或明确声明"未发现"

**Safety Rules**
- 必须对 Changelog 文件变更豁免结构化审查
- 标签操作失败不阻塞主流程，继续执行并记录异常
- 若 PR 描述缺失，必须在 What it does 中声明不完整
```

## 关键差异

| 差异点 | 原生 | PEVM |
|:-------|:----:|:----:|
| 审查质量 | 全面，4 Good / 2 Bad / 2 Ugly / 2 Test gaps / 3 Questions | 同等深度，4 Good / 2 Bad / 2 Ugly / 1 Test gap / 2 Questions |
| 结构 | 平铺 | 5 段分区（Flow/Input/Output/Dependencies/Safety） |
| Safety Rules | 无 | 5 条硬约束 |
| 错误处理 | 隐式 | 显式（标签失败不阻塞、API 超时降级） |
| "未发现"声明 | 无 | 每段必填 |
