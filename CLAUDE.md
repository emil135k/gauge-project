# Project Context

## Voice Interface Project (Jarvis)
- Building MCP-based voice interface for Claude Code
- TTS output (prefer Airy voice)
- STT input (currently using external voice-to-text)
- Goal: Hands-free CLI interaction

## User Preferences
- CLI-native workflow
- Voice-to-text input
- Former Unix sysadmin background
- Conversational + coding hybrid sessions

## Ideas & Notes
- MCP server for TTS integration
- Potential services: ElevenLabs, OpenAI TTS, Google Cloud TTS
- Investigate if Anthropic Airy voice is available via API
The YouTube video you linked is titled "Make Claude Code 100x BETTER (Context Engineering)" by the channel Kenny Liao.
This video discusses the concept of Context Engineering as the most important skill for getting better results from AI agents like Claude Code.
Here is a summary of the key points covered:
1. What is Context Engineering?
Definition: Context engineering is building dynamic systems to provide the right information and tools in the right format so that the Large Language Model (LLM) can plausibly accomplish a given task [02:27:27].
The Goal: Giving AI agents the relevant information at the right time to solve the exact task they are currently working on [02:44:42].
2. Why Context Engineering is Important (The Issues it Solves)
The video highlights three main issues with LLMs that context engineering helps to address:
Limited Context Window: Although context windows have grown, models are getting more capable and tasks are becoming more long-running, consuming more of this limited resource [03:04:41].
Context Rot: The performance of LLMs and AI agents degrades as the number of input tokens (context) increases. Removing irrelevant or distracting information significantly improves retrieval performance [03:55:00].
Needle in a Haystack Experiment: Performance decreases as the input text gets longer [04:25:22].
Long Mem Eval: Models perform better when given a focused prompt with only relevant parts of the conversation history, compared to the full history [05:43:24].
Attention Scarcity: Models, like humans, have a limited amount of attention. Giving them too much information spreads their attention thin, making them less focused on the task that actually matters [06:14:48].
3. Context Engineering in Practice
The video explores several practical techniques and components for effective context engineering:
System Prompts/Instructions: These include the main system prompt, tool definitions, and files like claude.md. This is for information Claude should always have top of mind [10:21:44].
Claude Code's official system prompt is detailed and includes instructions on its role, goals, and task management (using to-dos) [11:10:07].
System Reminders (User Messages): Information that gets injected as a user message at specific times to provide very targeted and focused context. The claude.md file is often injected this way [15:05:07].
Hooks: These are used to run logic and provide context dynamically, for example:
User Prompt Submit Hook: Runs every time a user submits a message (e.g., to make Claude aware of a memory system) [16:36:20].
Stop Hook: Gets triggered before Claude finishes its response (e.g., to ensure Claude updates its memory/context system after a conversation turn) [18:06:53].
Progressive Disclosure: Telling Claude it has access to tools or information but only loading the full definitions when it runs a command to read more (like using a CLI tool with a docs command instead of loading all tools via an MCP server into the system prompt) [22:23:44].
Sub-Agents: These are powerful because they have separate context windows (e.g., a researcher sub-agent with its own 200k context window). The main agent only sees the final, concise report, protecting its own context window from long intermediate tool results [25:35:10].
Memory/Context Systems: Persisting important information (like memories, project indices, or preferences) so Claude can reference it across sessions for a more consistent and reliable experience [27:39:21].
Compaction (/compact): A command that summarizes the entire conversation history into a shorter text, which helps keep conversations going for longer [29:15:20].
