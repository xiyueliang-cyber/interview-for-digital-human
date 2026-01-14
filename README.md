# Interview Agent for Digital Human

A Claude Code plugin designed to naturally collect life memories, personality clues, and authentic expressions through casual conversation — preparing material for future digital human simulation.

---

## Introduction

This plugin transforms Claude into a gentle, patient interviewer that helps preserve personal life stories in their most authentic form. Inspired by renowned interviewers like Studs Terkel (oral historian), Carl Rogers (humanistic psychologist), and Robert Caro (biographer), the agent conducts natural conversations that feel more like chatting with a friend than filling out a questionnaire.

The ultimate goal is **digital cloning**: collecting not just facts, but the unique way someone speaks, their emotional tones, and their attitudes toward people — authentic material that could enable a digital human to truly sound and feel like the original person.

This is a long-term, low-pressure approach. The agent never rushes to "complete" an interview, respects boundaries, and allows conversations to flow naturally.

---

## What This Plugin Does

### Core Capabilities

1. **Natural Interview Conversations**
   - Conducts warm, non-interrogative interviews using proven psychological and biographical techniques
   - Employs "micro-session" approach: asks 2-3 questions, then adapts based on user engagement
   - Never forces topics or creates pressure to share
   - Detects fatigue signals and gracefully ends sessions

2. **Strategic Question Types**
   - **Studs Terkel's "storytelling"**: "Tell me about..." rather than "What was..."
   - **Carl Rogers' "active listening"**: Repeats key phrases, shows empathy, encourages continuation
   - **Robert Caro's "scene reconstruction"**: Asks about sensory details (sights, sounds, smells), people present, specific moments
   - **Esther Perel's "layered inquiry"**: Moves from facts → feelings → relationships → meaning

3. **Original Expression Preservation**
   - Captures and reuses the user's unique phrases, idioms, and speaking style
   - Records emotional tones and casual speech patterns (e.g., "哈哈哈哈", "哼哼唧唧")
   - Never "corrects" colloquialisms into formal language
   - Preserves the exact wording for digital cloning purposes

4. **Dual-Track Recording System**
   - **Timeline Records** (`interview_records.csv`): Chronological life events with context
   - **Persona Insights** (`persona_insights.md`): Original expressions, personality clues, relationship attitudes, emotional patterns

5. **Intelligent Topic Planning**
   - Suggests conversation directions based on previous discussions
   - Avoids repetitive questioning
   - Balances structure with spontaneity

---

## Skills Overview

### 1. `interview-planner`
**Purpose**: Decides "what to talk about next"

- Selects interview directions (time periods, life themes)
- Avoids recently covered topics
- Keeps conversations feeling natural, not exhaustive

### 2. `interview-conversation`
**Purpose**: Conducts the actual interview

- Uses expert interviewing techniques (Terkel, Rogers, Caro, Perel)
- Adapts to user engagement (continues when interested, stops when tired)
- Captures original expressions in real-time
- Reconstructs complete scenes with sensory details

### 3. `interview-log-writer`
**Purpose**: Records key information after sessions

- Extracts 1-3 key memories per session
- Saves timeline records to CSV
- Triggers persona insights collection for character-revealing moments
- Never interrupts active conversations

### 4. `persona-insights-writer` (Background)
**Purpose**: Extracts personality clues and speaking patterns

- Preserves original phrasings and expressions
- Records behavioral observations (not psychological analysis)
- Documents how the person talks about important people
- Captures emotional tones and sentiments

---

## MCP Tools Required

**None**

This plugin currently saves all data to local files:
- `interview_records.csv` - Timeline of life events
- `persona_insights.md` - Personality insights and original expressions

*(Future versions may integrate with Google Sheets MCP for cloud storage)*

---

## Example Use Cases

### 1. **Preserving a Parent's Life Story**
> Your mother is getting older, and you want to preserve her stories, her unique way of speaking, and her wisdom for future generations.

**How it helps:**
- Natural, ongoing conversations (not one exhausting session)
- Captures her exact phrases and expressions
- Records sensory details that bring memories alive
- Prepares material for a potential digital simulation that could "speak" like her

### 2. **Creating a Personal Digital Legacy**
> You want to leave behind more than photos — you want future generations to know how you thought, spoke, and saw the world.

**How it helps:**
- Documents your personality through your own words
- Captures your attitudes toward important people and events
- Preserves your speaking style and emotional patterns
- Builds a comprehensive archive over time, not all at once

### 3. **Biographical Research**
> You're writing a memoir or helping someone else write theirs.

**How it helps:**
- Employs professional biographical interview techniques
- Reconstructs complete scenes with rich details
- Organizes memories chronologically
- Flags areas for follow-up questioning

### 4. **Family History Documentation**
> You want to document family stories before they're lost.

**How it helps:**
- Makes the process feel like pleasant family conversations
- Records stories in the speaker's authentic voice
- Captures relationships and emotional contexts
- Suggests new directions based on previous stories

### 5. **Digital Human Development**
> You're working on AI/digital human projects and need authentic human data.

**How it helps:**
- Collects speaking patterns and personality traits
- Documents relationship dynamics and emotional responses
- Preserves original expressions for training data
- Maintains ethical, consent-based collection process

---

## Sample Conversation Flow

```
Agent: "能给我讲讲你小时候住的地方吗？那里是什么样子的？"

User: "前院花台，那里有枇杷树和海棠树"

Agent: "前院花台...（重复）你还记得那里的样子吗？"

User: "春天会有白色小花，爬山虎爬满了长廊，阳光会透过叶子缝隙掉下来"

Agent: "阳光透过叶子缝隙...那画面一定很美。你经常去那里吗？"
```

**What's captured:**
- Timeline: "Childhood memory of front yard garden with loquat and crabapple trees"
- Original expression: "阳光会透过叶子缝隙掉下来"
- Emotional tone: Warm nostalgia for childhood place
- Sensory details: Visual (white flowers, climbing ivy, dappled sunlight)

---

## Design Philosophy

### Conversation-First, Structure-Later
The agent prioritizes natural flow over systematic coverage. It's okay to skip topics or revisit them multiple times.

### No Pressure, No Interrogation
If the user doesn't want to talk about something, the agent immediately pivots. The goal is comfort, not completeness.

### Long-Term Collection
This isn't a one-time interview. The agent is designed for ongoing conversations over weeks, months, or years.

### Preserve Authenticity
Original wording matters more than polished language. "哼哼唧唧" is better than "reluctantly complied."

### Respect and Consent
The agent never manipulates, never pushes sensitive topics, and always allows the user to control the pace and direction.

---

## Future Development

- Google Sheets MCP integration for cloud backup
- Multi-language support
- Voice tone and emotion analysis
- Integration with digital human rendering systems
- Advanced timeline visualization

---

## Getting Started

1. Place this plugin in your Claude Code plugins directory
2. Start a conversation: Just say "hi" or "我们聊聊"
3. The agent will naturally guide you into sharing stories
4. Find your records in:
   - `interview_records.csv` (timeline)
   - `persona_insights.md` (personality insights)

---

## Credits

**Interview Techniques Inspired By:**
- **Studs Terkel** - Oral history and storytelling approach
- **Carl Rogers** - Active listening and unconditional positive regard
- **Robert Caro** - Biographical scene reconstruction
- **Esther Perel** - Layered inquiry and relational depth

**Designed for:** Digital human preservation, family history, biographical research, and personal legacy creation.
