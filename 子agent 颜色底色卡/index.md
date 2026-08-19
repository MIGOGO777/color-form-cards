# 子agent 颜色底色卡

这组卡片给叶子 Agent 使用，不替代主 Agent 的完整形态蓝图。

## 入口

- [[Green Explorer Lite|Green Explorer Lite]]
- [[Blue Researcher Lite|Blue Researcher Lite]]
- [[Red Architect Lite|Red Architect Lite]]
- [[Purple Builder Lite|Purple Builder Lite]]

## 使用规则

- 主 Agent 负责判断当前任务该挂哪种颜色；叶子不自行切色或继续派发。
- 调用必须满足现行多 Agent 授权协议：可以来自用户的明确授权，或 颜色路由 Skill 对绿、蓝、红只读工作单的逐次隐式授权。后者不扩大到紫色、DeepSeek、写入或高风险任务。
- 一次派发只挂一种主底色，并补齐任务范围、输入、读写边界、禁止事项和验收标准。
- 绿、蓝、红分别返回 `Option Set`、`Evidence Packet`、`Decision Packet`；红色前置不足时返回 `Decision Gap`。
- 回执中的 `suggested_next_color` 或 `needed_color` 只是建议。是否串联下一颜色由主 Agent 决定并重新派发。
- 需要编码、调试、批量修改时使用 `Purple Builder Lite`；紫色内容本轮不变。

## 分工边界

- `思维形态 Blueprints/`：给主 agent 切换思维形态。
- `子agent 颜色底色卡/`：给叶子 Agent 设定轻量工作底色和类型化回执。
