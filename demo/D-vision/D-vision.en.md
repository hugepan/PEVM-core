# D-Vision: From "Everything Is a Card" to "The Card Is a File"

> **This is not a product claim — it's a direction projection validated by working code.**
>
> pevm mount mounts cards into the filesystem. D-Vision asks: what if these were native Linux capabilities?

---

## 1. Existing Prototypes

### pevm mount — Cards in the Filesystem

```bash
pevm mount /mnt/card

ls /mnt/card/ | head
→ 李白.yqf  杜甫.yqf  熵.yqf  螺丝.yqf  001·建域.yqf  ...

grep "register: 9" /mnt/card/*.yqf
→ Cross-card search, standard Unix tools, zero configuration
```

Equivalent to: `/proc/` maps processes to files, `/card/` maps entities to files. **No new tools needed — the entire Unix toolbox becomes a cognitive analysis toolkit.**

### pevm query — Card Query Tool

```bash
pevm query 李白
→ Name: Li Bai  Era: Tang Dynasty  Style: Green Lotus · Immortal Poet · Banished Immortal
  Cognitive Level: Top Authority — Domain Foundational (9)

pevm query 李白 --neighbors 5
→ Screw 52%  Plato 36%  ...
```

---

## 2. Vision: The Protocol Layer for AI-native Linux

### Core Proposition

In 2026, academia and industry are simultaneously charging toward "AI-native OS" from different directions:

| Project | What It Does |
|---------|-------------|
| **Anima OS** | Bare-metal x86_64 OS, LLM logit as kernel-level security primitive |
| **SchedCP** | LLM agent auto-optimizes Linux scheduler |
| **KernelAGI** | LKM module for kernel-space AI inference |
| **Quine** | LLM agent = native POSIX process (PID/streams/fork/exec) |
| **NexusOS** | Open-source, "model is in the kernel" |

**Everyone is "putting LLMs into the OS" — but nobody is defining "how entities are encoded for the LLM to read."**

YQF format + PEVM protocol layer is that piece. PEVM is to AI-native Linux what HTTP is to the internet.

### Architectural Vision

```
Traditional Linux:           AI-native Linux (hypothetical):
  VFS (everything is file)     VFS + card_fs (everything is card)
  /proc/[pid]/status           /card/[name].yqf
  rwx permissions              rwx + s(simulate) + w(weld) + d(deploy)
  No system LLM                llmd (LLM system daemon)
```

Not "PEVM = Linux" — it's "Linux + PEVM = AI-native Linux." PEVM defines the protocol layer; the OS integration layer is left to collaborators.

### Hypothetical card_fs Embedded in VFS

```c
// Hypothetical syscall — not current implementation
int card_open(const char *name, int flags);

// /card/ namespace
/card/李白                      → character card
/card/熵                       → concept card
/card/3融-孔子×老子×但丁       → fusion card
/card/by-domain/               → domain index
```

pevm mount has already proven this pattern at the user-space level. A FUSE version is ready — the next step is the card_fs FUSE mount implementation.

---

## 3. Roadmap

```
Phase 1 (Complete) — Proof of Concept:
  ☑ pevm mount: card → filesystem
  ☑ pevm query prototype: natural language / JSON / neighbors output

Phase 2 (In Progress) — Real Mount:
  ☐ card_fs FUSE: mount to /mnt/card/, real-time read/write

Phase 3 (Vision) — AI-native Linux:
  ☐ card_fs → VFS kernel module
  ☐ llmd → LLM system daemon
```

---

*Currently runnable code: two CLI tools — `pevm mount` and `pevm query`.*
