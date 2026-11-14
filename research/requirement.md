## 研究过程要求

IMPORTANT: Agents 应当设定 Hooks，按本要求检查研究文档是否得到维护。

研究文档、实验分析、论文、研究笔记和科研邮件统一遵循 [Scientific Writing & Editing Protocol](scientific-writing-protocol.md)。`log.md` 保留按时间追加的执行记录；讲解和结论按科学问题与证据链重新组织。

实验代码遵循 `ml-experiment/repo-requirement.md`。研究文档通过 run id、W&B 链接引用实验，不复制实验内容。

### 目录结构

```text
research/
├── <theory>.md        # 理论总文档，多个主题属于同一理论时创建
└── <topic>/           # 一个研究问题一个目录
    ├── README.md      # 研究问题与主要进展
    ├── log.md         # 执行进展
    └── writeup/       # 理论讲解，见 writeup-requirement.md
```

### 文件规范

- **`README.md`**：开头写研究问题、假设、评测指标、停止标准，这部分由人确认后再改。下面列当前结论，每条附证据（run id 或图）；被推翻的结论用删除线保留。
- **`log.md`**：按时间只追加。每条写时间、做了什么（commit、run id）、结果、下一步。失败的尝试也要记。
- **`writeup/`**：带交互动画的博客式理论讲解，要求见 `writeup-requirement.md`。
- **`<theory>.md`**：讲各主题如何组成一套理论。每个主题写一段摘要并链接其 `writeup/index.html`，不复制内容。

### Hooks 检查

| 触发 | 检查 | 不通过 |
| --- | --- | --- |
| `Stop`：本回合有实验运行 | `log.md` 有新条目 | 阻止 |
| `Stop`：`README.md` 结论有改动 | `writeup/index.html` 也有改动 | 提醒 |
| `Stop` | 文档中引用的图片和链接都存在 | 阻止 |
