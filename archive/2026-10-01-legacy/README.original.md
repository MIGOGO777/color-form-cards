# 🎨 颜色形态卡 Color Form Cards

一套给 AI Agent 使用的**颜色化思维形态系统**：把「探索 / 研究 / 决策 / 建造」四种工作形态映射为 🟢🔵🔴🟣 四种颜色，用户一句话即可切换 Agent 的思维模式。灵感来自假面骑士空我（Kamen Rider Kuuga）的形态切换——用颜色标识，干净利落。

## 🎮 核心概念

| 颜色 | 形态 | 蓝图 | 职责一句话 | 触发词 |
|------|------|------|-----------|--------|
| 🟢 绿 | Explorer | `思维形态 Blueprints/Explorer.md` | 改变**选项空间**：挑战假设、重构问题、看见更多可能 | 绿 / 变绿 |
| 🔵 蓝 | Researcher | `思维形态 Blueprints/Researcher.md` | 改变**相信程度**：命题化、证据分级、因果核验 | 蓝 / 变蓝 |
| 🔴 红 | Architect | `思维形态 Blueprints/Architect.md` | 改变**行动状态**：收敛选项、形成可执行承诺 | 红 / 变红 |
| 🟣 紫 | Builder | `思维形态 Blueprints/Builder.md` | 改变**系统状态**：严谨建造、最小修改、步步为营 | 紫 / 变紫 |
| ⚪ 白 | — | 日常模式 | 默认形态，自由切换 | 白 / 变白 |

> 参考映射：绿·天马、蓝·青龙、红·全能 / 泰坦、紫·泰坦（空我的形态语言）

## 📁 两层结构

- **`思维形态 Blueprints/`** — 完整思维形态蓝图，给**主 Agent** 切换思维模式。每份含 Mission / 何时进入 / 核心动作 / 自适应深度与停止门 / 交付 / 边界纪律。
- **`子agent 颜色底色卡/`** — 精简工作卡（Lite），给**叶子 Agent** 设定轻量工作底色 + 类型化回执（`Option Set` / `Evidence Packet` / `Decision Packet` / `Decision Gap`），不替代主 Agent 的完整形态蓝图。

## ✨ 设计要点

- **独立自洽**：每份蓝图单独加载即满血，匹配「开新会话挂不同色」的用法。
- **越界不自动交接**：遇到不归本形态的问题，直接指出「这问题适合 X 色」，由用户转达给对应实例；叶子 Agent 只向主 Agent 回执。
- **结构化回执**：每个叶子形态返回固定字段的包，`suggested_next_color` / `needed_color` 只作建议，是否串联下一颜色由主 Agent 决定并重新派发。
- **自适应深度**：不设全局固定的路径数 / 层级数 / 打分表；问题越小回执越轻，以信息增益和判断影响决定何时停止。
- **黑色形态**：`思维形态 Blueprints/Claude黑色施工形态.md` 是 Claude 作为 Codex 直接管理的独立施工员时使用的受限施工协议（任务包驱动、最小修改、失败显性化）。

## 📄 文件清单

```
color-form-cards/
├── README.md
├── 思维形态 Blueprints/
│   ├── index.md
│   ├── Explorer.md          # 🟢 绿 · 选项探索者
│   ├── Researcher.md        # 🔵 蓝 · 证据审计者
│   ├── Architect.md         # 🔴 红 · 决策收敛者
│   ├── Builder.md           # 🟣 紫 · 开发与多代理协同协议
│   └── Claude黑色施工形态.md # ⚫ 黑 · 受限施工协议
└── 子agent 颜色底色卡/
    ├── index.md
    ├── Green Explorer Lite.md    # 🟢 返回 Option Set
    ├── Blue Researcher Lite.md   # 🔵 返回 Evidence Packet
    ├── Red Architect Lite.md     # 🔴 返回 Decision Packet / Decision Gap
    └── Purple Builder Lite.md    # 🟣 修改交付回执
```

## 📝 使用

1. 主 Agent 判断当前任务该挂哪种颜色。
2. 主 Agent 说话时「变绿 / 变蓝 / 变红 / 变紫 / 变白」即切换思维形态。
3. 派发叶子 Agent 时挂一张对应颜色的 Lite 卡，补齐任务范围、输入、读写边界、禁止事项和验收标准。
4. 叶子返回类型化回执（`Option Set` / `Evidence Packet` / `Decision Packet`）；主 Agent 根据 `suggested_next_color` 决定是否串联下一颜色。