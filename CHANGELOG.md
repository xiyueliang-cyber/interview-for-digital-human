# Changelog

All notable changes to the Interview for Digital Human plugin will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.0.0] - 2026-01-13

### Added
- **interview-conversation skill**: Natural conversation agent with expert interviewing techniques
  - Studs Terkel's storytelling approach
  - Carl Rogers' active listening
  - Robert Caro's scene reconstruction
  - Esther Perel's layered inquiry
  - Micro-session approach (2-3 questions per round)
  - Engagement signal detection (continues/stops based on user interest)

- **interview-planner skill**: Intelligent topic planning
  - Selects conversation directions based on context
  - Avoids repetitive topics
  - Suggests time periods or life themes

- **interview-log-writer skill**: Timeline recording system
  - Extracts 1-3 key memories per session
  - Saves to configured storage (Workspace or Google Sheets)
  - Captures: time period, people, events, emotions, and notes

- **persona-insights-writer skill**: Personality and expression preservation
  - Original expressions and phrasings
  - Personality clues (habits, preferences)
  - Relationship dynamics
  - Emotional tones and sentiments
  - Collection notes for future follow-up

- **Documentation**:
  - Comprehensive README with use cases
  - CLAUDE.md with role definition
  - Sample data structures

- **Data Storage**:
  - Multiple storage backends: Workspace (XYZ platform) and Google Sheets
  - `interview_records`: Chronological timeline of life events
  - `persona_insights`: Original expressions and personality insights

### Features
- Long-term, low-pressure conversation approach
- Preserves authentic speaking style for digital human simulation
- Respects user boundaries and fatigue signals
- No psychological analysis or evaluation
- Designed for biographical research and family history preservation

---

## Future Roadmap

### Planned Features
- Enhanced multi-language support
- Voice tone and emotion analysis integration
- Timeline visualization
- Advanced search and filtering of memories
- Export to various formats (JSON, PDF)
- Additional storage backends

### Under Consideration
- Integration with digital human rendering systems
- Collaborative family history collection
- AI-assisted memory prompting
- Photo and document attachment support
