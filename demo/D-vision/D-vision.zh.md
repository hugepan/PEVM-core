# D 层愿景：从"万物皆卡"到"卡即文件"

> **这不是一个产品 claim——这是一个经过代码验证的方向推演。**
>
> pevm mount 把卡挂到文件系统。D 层是问：如果这些是 Linux 的原生能力呢？

---

## 1. 已有原型

### pevm mount —— 卡在文件系统中

```bash
pevm mount /mnt/card

ls /mnt/card/ | head
→ 李白.yqf  杜甫.yqf  熵.yqf  螺丝.yqf  001·建域.yqf  ...

grep "register: 9" /mnt/card/*.yqf
→ 跨卡搜索，标准 Unix 工具，零配置
```

等价于：`/proc/` 把进程映射为文件，`/card/` 把实体映射为文件。**不需要新工具——整个 Unix 工具箱自动成为认知分析工具。**

### pevm query —— 卡片查询工具

```bash
pevm query 李白
→ 姓名：李白  时代：盛唐  别号：青莲居士 · 诗仙 · 谪仙人
  认知层级：顶尖权威——领域奠基级（9）

pevm query 李白 --neighbors 5
→ 螺丝 52%  柏拉图 36%  ...
```

---

## 2. 愿景：AI-native Linux 的协议层

### 核心命题

2026 年，学术界和工业界从不同方向同时冲向"AI-native OS"：

| 项目 | 做什么 |
|------|--------|
| **Anima OS** | 裸机 x86_64 OS，LLM logit 作为内核级安全原语 |
| **SchedCP** | LLM agent 自动优化 Linux 调度器 |
| **KernelAGI** | LKM 模块做内核空间 AI 推理 |
| **Quine** | LLM agent = 原生 POSIX 进程 |
| **NexusOS** | 开源，"model is in the kernel" |

**大家都在做"把 LLM 放进 OS"——但没人定义"OS 的实体怎么编码给 LLM 看。"**

YQF 格式 + PEVM 协议层就是那一块。PEVM 之于 AI-native Linux，就像 HTTP 之于互联网。

### 架构想象

```
传统 Linux：                AI-native Linux（假想）：
  VFS（万物皆文件）          VFS + card_fs（万物皆卡）
  /proc/[pid]/status        /card/[name].yqf
  rwx 权限                  rwx + s(模拟) + w(焊接) + d(部署)
  无系统 LLM                llmd（LLM 系统守护进程）
```

不是"PEVM = Linux"——是"Linux + PEVM = AI-native Linux。" PEVM 定义了协议层，OS 集成层留给合作者。

### card_fs 嵌入 VFS 的假想

```c
// 假想系统调用——不是当前实现
int card_open(const char *name, int flags);

// /card/ 命名空间
/card/李白          → 人物卡
/card/熵           → 概念卡
/card/3融-孔子×老子×但丁  → 融合卡
/card/by-domain/   → 按域索引
```

pevm mount 已经证明了这个模式在用户态可行。FUSE 版本已准备就绪——下一步是 card_fs FUSE 挂载实现。

---

## 3. 路线图

```
Phase 1（已完成）——概念验证：
  ☑ pevm mount：卡→文件系统
  ☑ pevm query 原型：自然语言/JSON/neighbors 输出

Phase 2（进行中）——真实挂载：
  ☐ card_fs FUSE：挂载到 /mnt/card/，实时读写

Phase 3（愿景）——AI-native Linux：
  ☐ card_fs → VFS 内核模块
  ☐ llmd → LLM 系统守护进程
```

---

*当前可运行的代码：`pevm mount` 和 `pevm query` 两个 CLI 工具。*
