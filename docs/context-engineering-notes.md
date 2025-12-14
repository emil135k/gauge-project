# Context Engineering Notes

Source: "Make Claude Code 100x BETTER (Context Engineering)" by Kenny Liao (YouTube)

## What is Context Engineering?

**Definition:** Building dynamic systems to provide the right information and tools in the right format so that the LLM can plausibly accomplish a given task.

**Goal:** Giving AI agents the relevant information at the right time to solve the exact task they are currently working on.

## Why It Matters (Problems It Solves)

1. **Limited Context Window** - Models are more capable, tasks are longer-running, consuming more of this limited resource.

2. **Context Rot** - LLM performance degrades as input tokens increase. Removing irrelevant information improves retrieval performance.

3. **Attention Scarcity** - Models have limited attention. Too much information spreads attention thin, reducing focus on the actual task.

## Techniques in Practice

### System Prompts/Instructions
- Main system prompt, tool definitions, CLAUDE.md files
- Information Claude should always have top of mind

### System Reminders (User Messages)
- Injected at specific times for targeted context
- CLAUDE.md often injected this way

### Hooks
- **User Prompt Submit Hook**: Runs on every user message (e.g., inject memory awareness)
- **Stop Hook**: Runs before Claude finishes (e.g., update memory system)

### Progressive Disclosure
- Tell Claude tools/info exist, but only load full definitions when requested
- CLI with docs command vs loading everything via MCP upfront

### Sub-Agents
- Separate context windows (e.g., researcher agent with own 200k context)
- Main agent only sees final concise report
- Protects main context from long intermediate results

### Memory/Context Systems
- Persist important information across sessions
- Memories, project indices, preferences

### Compaction (/compact)
- Summarizes conversation history into shorter text
- Keeps conversations going longer
