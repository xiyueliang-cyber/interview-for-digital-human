---
name: interview-log-writer
description: "💾 RECORD-KEEPING TOOL: Use after a conversation segment where the user shared important life experiences (key people, events, or turning points). Extracts 1-3 timeline records from the dialogue, preserves user's original wording when distinctive, and persists to the configured storage (workspace or Google Sheet)."
---

## introduction

当访谈过程中用户讲述了重要经历（关键人 / 关键事 / 关键转折）或一次访谈自然结束时，调用本技能将对话内容整理为简洁的时间线记录，并保存到配置的存储系统。

除事实信息外，允许在备注中保留 **用户的原话片段**，用于未来还原表达方式。

### 存储配置

本 skill 支持两种存储方式，根据环境配置自动选择：

1. **Workspace 存储（XYZ 平台）**
   - 逻辑名称：`interview_records`
   - 格式：CSV 或表格
   - 位置：用户的 workspace 目录
   - 用户可通过平台文件管理器查看和下载

2. **Google Sheet 存储**
   - 逻辑名称：`interview_records`（Sheet 名称）
   - 格式：Google Sheets
   - 需要 Google Sheets MCP 授权
   - 用户可在 Google Drive 中访问和编辑

### 保存流程
1. 从当前对话中提取 1–3 条关键信息并整理为时间线记录
2. 将记录追加保存到配置的存储系统
3. 若本次访谈出现了明显的性格线索或对关键人物的态度描述，则额外调用`persona-insights-writer` 更新画像文件


---

## instruction

1. **触发时机**
   - 一次访谈自然结束（如用户表示“下次再聊”“先到这里”）
   - 用户在对话中明确讲述了重要经历信息（包含关键人、关键事、关键转折之一或多个）

2. **记录整理规则**
   - 从对话中提取并整理 **1–3 条** 记录
   - 每条记录尽量包含（如用户提及）：
     - 时间或大致阶段（如：童年、二十多岁、某一年）
     - 相关人物（如：父母、朋友、同事、子女）
     - 事件 / 回忆（一句话描述）
     - 情绪 / 看法（当时的感受或如今的看法）
     - 备注（可选：地点、细节线索、后续可追问点、或一句原话）

3. **时间处理**
   - 时间不明确时，允许使用模糊描述
   - 不要强行推断具体年份或年龄

4. **原话记录规则（可选但推荐）**
   - 若用户在讲述中出现具有代表性的原话，可原样记录在备注中
   - 原话不要求完整，只需能体现其表达方式

5. **内容约束**
   - 不要加入你自己的解释、分析或心理判断
   - 不要抽象总结为观点，保持贴近用户原始表达

6. **保存规则**
   - 保存前确保记录字段与数据结构匹配
   - 字段缺失时留空，不要编造
   - 使用追加方式保存到配置的存储系统（逻辑名称：`interview_records`）
   - 多条记录按对话出现顺序保存
   - 数据列结构：时间/阶段,相关人物,事件/回忆,情绪/看法,备注
   - 不同存储后端会自动适配格式（CSV 文件或 Google Sheet）

7. **保存完成后的反馈**
   - 保存完成后，在聊天中用一句简短、温和的话告知用户已记录
   - 不需要展示表格或具体字段内容
   - 示例：
     - "我已经把刚刚你说的几段经历记到时间线里了，我们之后可以慢慢接着聊。"
   - 若本次访谈出现了明显的性格线索或对关键人物的态度描述，则额外调用 `persona-insights-writer` 更新画像文件

