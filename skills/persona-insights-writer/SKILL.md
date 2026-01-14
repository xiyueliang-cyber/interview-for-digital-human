---
name: persona-insights-writer
description: 从访谈对话中提取性格线索和原始表达，保存为数字人模拟的真实材料
---

## introduction

1. plugin 指的是 Claude code plugin 组件
2. capability 指 XYZ 平台中的 Interview Capability
3. 该 skill 用于从访谈中提取和累积：
   - 用户的原始表达和措辞（为数字人模拟准备材料）
   - 性格线索、习惯、偏好（观察，非诊断）
   - 对重要人物的态度
   - 情感色彩和语气
4. 这是一个辅助性、长期累积的模块，不是访谈的主流程

你的角色是 **传记作家的助手**，而不是心理分析师
你的任务是：
- 保留用户真实的表达方式
- 记录观察到的行为模式
- 不做心理诊断或标签化

## instruction

1. **触发时机**
   - 由 `interview-log-writer` 在访谈结束时调用
   - 仅当本次访谈中出现以下内容之一时才需要记录：
     - 特色的表达方式或措辞（如："老财迷"、"心情也很美"）
     - 明显的性格特征或习惯（如：喜欢存钱、经常忘记带东西）
     - 价值观或偏好（如：最喜欢春天、不喜欢人多）
     - 对关键人物的描述或态度
     - 情感色彩明显的回忆

2. **核心原则**
   - **保留原话**：用引号标注用户的原始表达，不要改写或美化
   - **观察，不判断**：记录行为模式，不做心理分析
   - **传记风格**：像记录传记素材，不像写心理评估
   - **真实性优先**：口语化、不完整的句子也要保留

3. **提取内容类型**

   **🗣️ Original Expressions & Phrasings**
   - 用户独特的说法、口头禅、特色表达
   - 描述事物的特定方式
   - 情感词汇和语气词（如："哈哈哈哈"、"挺"、"也很"）
   - 示例：
     ```
     - **"老财迷"**
       - Context: 描述自己小学时喜欢存零花钱
       - Source: 小学时期回忆
       - Date: 2026-01-09
     ```

   **💭 Personality Clues（习惯与倾向 / 偏好）**
   - 从行为、习惯中观察到的特质
   - 必须包含 `Original` 字段（用户原话）
   - 示例：
     ```
     - **喜欢存钱**
       - Original: "喜欢存零花钱老财迷"、"单纯喜欢存钱的感觉"
       - Context: 小学时不去小卖店买零食，而是把零花钱存起来
       - Source: 小学时期回忆
       - Date: 2026-01-09
     ```

   **👨‍👩‍👧 People & Relationships**
   - 如何谈论和描述重要人物
   - 保留对人物的原始描述
   - 示例：
     ```
     ### 父亲
     - **喜欢海棠花**
       - Original: "我爸特别喜欢开花的时候 逢人就夸"
       - Context: 童年前院有海棠树
       - Source: 童年时期回忆
       - Date: 2026-01-09
     ```

   **🌸 Emotional Tones & Sentiments**
   - 对某段时期、地点、经历的情感色彩
   - 记录语气（Tone）：温暖、怀念、期待、开心等
   - 示例：
     ```
     - **对童年前院花台的怀念**
       - Original: "前院花台"、"春天会有白色小花"
       - Context: 童年最喜欢待的地方
       - Tone: 温暖、宁静
       - Date: 2026-01-09
     ```

4. **文件格式与结构**
   - 保存到项目根目录的 `persona_insights.md`
   - 使用 Markdown 格式
   - 分为四大类：
     1. 🗣️ Original Expressions & Phrasings
     2. 💭 Personality Clues（含：习惯与倾向 / 偏好）
     3. 👨‍👩‍👧 People & Relationships（按人物分组）
     4. 🌸 Emotional Tones & Sentiments
   - 每个类别的末尾有一个 📝 Collection Notes 区域

5. **更新规则**
   - 首次运行时创建完整的文件结构
   - 后续运行时追加新内容到对应分类下
   - **保持时间顺序**：新记录添加到每个分类的末尾
   - 如果发现相似的表达或线索，可以：
     - 补充到已有记录中（在同一条目下添加新的 Original 引用）
     - 或创建新条目（如果表达方式不同或上下文不同）

6. **内容约束**
   - ✅ 保留口语化表达（"哈哈哈哈"、"挺"、"也"等）
   - ✅ 保留不完整的句子（如用户说话时的停顿、跳跃）
   - ✅ 记录语气和情绪（通过标点、语气词推断）
   - ❌ 不要做心理分析或诊断
   - ❌ 不要给用户贴标签（如：内向型、完美主义者）
   - ❌ 不要推断因果关系
   - ❌ 不要评价好坏
   - ❌ 不要把口语改写成书面语

7. **📝 Collection Notes（可选）**
   - 在访谈积累一定量后，可以在此区域添加元笔记：
     - 记忆特点（如：对视觉细节记忆清晰）
     - 表达风格（如：口语化、常用短句）
     - 可追问方向（如：童年其他场景、小学朋友）
   - 不需要每次都更新，只在有新的整体观察时添加

8. **完成后的反馈**
   - 更新完成后，不需要向用户反馈
   - 这个过程对用户是透明的，只在后台默默记录
   - 不要打断访谈流程

---

## 文件结构模板

```markdown
# Persona Insights Collection
> Material for digital-human simulation, collected through natural conversation

---

## 🗣️ Original Expressions & Phrasings
> Key words, phrases, and ways of describing things — preserved as spoken

- **"原话内容"**
  - Context: 在什么情境下说的
  - Source: 来源时期
  - Date: 记录日期

---

## 💭 Personality Clues
> Behavioral patterns, habits, preferences — not diagnoses, just observations

### 习惯与倾向

- **观察到的特质**
  - Original: "用户原话"
  - Context: 具体情境描述
  - Source: 来源时期
  - Date: 记录日期

### 偏好

- **偏好内容**
  - Original: "用户原话"
  - Context: 具体情境描述
  - Source: 来源时期
  - Date: 记录日期

---

## 👨‍👩‍👧 People & Relationships
> How they talk about important people in their life

### 人物名称

- **关系特点**
  - Original: "用户原话"
  - Context: 具体情境描述
  - Source: 来源时期
  - Date: 记录日期

---

## 🌸 Emotional Tones & Sentiments
> How they feel/felt about certain periods, places, or experiences

- **情感描述**
  - Original: "用户原话"
  - Context: 具体情境描述
  - Tone: 情感色彩（如：温暖、怀念）
  - Date: 记录日期

---

## 📝 Collection Notes
> Meta-notes for the interviewer/system

- **记忆特点**：整体观察
- **表达风格**：语言特点
- **可追问方向**：未来访谈建议
```
