# Graph Report - .  (2026-05-16)

## Corpus Check
- Corpus is ~7,164 words - fits in a single context window. You may not need a graph.

## Summary
- 182 nodes · 202 edges · 19 communities (18 shown, 1 thin omitted)
- Extraction: 94% EXTRACTED · 6% INFERRED · 0% AMBIGUOUS · INFERRED: 13 edges (avg confidence: 0.75)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- [[_COMMUNITY_Tool Calling Strategies|Tool Calling Strategies]]
- [[_COMMUNITY_Core Agent|Core Agent]]
- [[_COMMUNITY_Architecture Concepts|Architecture Concepts]]
- [[_COMMUNITY_Persistent Memory|Persistent Memory]]
- [[_COMMUNITY_Session Database|Session Database]]
- [[_COMMUNITY_Context Compression|Context Compression]]
- [[_COMMUNITY_Skill Loader|Skill Loader]]
- [[_COMMUNITY_Tool Calling Base|Tool Calling Base]]
- [[_COMMUNITY_Tool Registry|Tool Registry]]
- [[_COMMUNITY_Skills Manager|Skills Manager]]
- [[_COMMUNITY_CLI & Prompt Builder|CLI & Prompt Builder]]
- [[_COMMUNITY_Session Recall|Session Recall]]
- [[_COMMUNITY_Prompt Caching|Prompt Caching]]
- [[_COMMUNITY_File Tools|File Tools]]
- [[_COMMUNITY_Memory Tool|Memory Tool]]
- [[_COMMUNITY_Terminal Tool|Terminal Tool]]
- [[_COMMUNITY_Tools Init|Tools Init]]

## God Nodes (most connected - your core abstractions)
1. `Agent` - 15 edges
2. `SessionDB` - 12 edges
3. `main()` - 10 edges
4. `ToolCallingStrategy` - 9 edges
5. `TextStrategy` - 9 edges
6. `CLI Interface` - 9 edges
7. `StructuredStrategy` - 8 edges
8. `PersistentMemory` - 8 edges
9. `ContextCompressor` - 7 edges
10. `SessionRecall` - 7 edges

## Surprising Connections (you probably didn't know these)
- `Agent` --uses--> `ToolCallingStrategy`  [INFERRED]
  agent.py → tool_calling.py
- `main()` --calls--> `Agent`  [INFERRED]
  cli.py → agent.py
- `main()` --calls--> `SessionDB`  [INFERRED]
  cli.py → memory/session_db.py
- `main()` --calls--> `PersistentMemory`  [INFERRED]
  cli.py → memory/persistent.py
- `main()` --calls--> `SkillLoader`  [INFERRED]
  cli.py → skills/loader.py

## Communities (19 total, 1 thin omitted)

### Community 0 - "Tool Calling Strategies"
Cohesion: 0.1
Nodes (13): _format_tools_as_text(), _parse_tool_json(), ParsedToolCall, Tool-Calling Strategies (Chapter 3b)  Two strategies for tool calling depending, Try to parse one or more tool calls from a raw string., Render tool schemas as plain-text instructions for the system prompt., For models that emit tool calls as text (Gemma, LLaMA, etc.)., A tool call extracted from a model response, regardless of format. (+5 more)

### Community 1 - "Core Agent"
Cohesion: 0.13
Nodes (9): Agent, Mini-Hermes Agent (Chapters 3, 6, 13, 14)  Core agent loop with: - Tool calling, Make one API call with tool schemas., Prepare messages for API call, stripping internal fields., Core agent loop: message -> tools -> response., Fork a review agent on a background thread (Chapter 13)., Set the ContextCompressor (Chapter 14)., Enable prompt caching (Chapter 6). Only useful for Anthropic models. (+1 more)

### Community 2 - "Architecture Concepts"
Cohesion: 0.13
Nodes (15): Core Agent, CLI Interface, Context Compression, Memory Module, Prompt Builder, Prompt Caching, Skills Module, Tool Calling (+7 more)

### Community 3 - "Persistent Memory"
Cohesion: 0.14
Nodes (7): PersistentMemory, Persistent Memory (Chapter 8)  MEMORY.md and USER.md files -- frozen snapshot lo, Load both files as a combined context block (frozen snapshot)., Append an observation to MEMORY.md (writes to disk only)., Replace the user profile (writes to disk only)., Read current memory contents., Read current user profile.

### Community 4 - "Session Database"
Cohesion: 0.16
Nodes (4): Session Database (Chapter 7)  SQLite + FTS5 for episodic memory. Stores every co, Full-text search across all sessions., Clean user input for FTS5 safety., SessionDB

### Community 5 - "Context Compression"
Cohesion: 0.21
Nodes (6): ContextCompressor, flush_memories(), Context Compression (Chapter 14)  Middle-out compression: protect head + tail, s, Give the agent one turn to save memories before compression.      Appends a user, Compress if approaching context window limit.          Returns the (possibly com, Get the most recent messages fitting within max_tokens.

### Community 6 - "Skill Loader"
Cohesion: 0.21
Nodes (6): Skill Loader (Chapter 10)  Discover SKILL.md files in folders, parse frontmatter, Load all skill folders, return name + description + body + path., Build summary index for system prompt (tier 1: metadata only)., Find a skill by name., Split YAML frontmatter from markdown body., SkillLoader

### Community 7 - "Tool Calling Base"
Cohesion: 0.2
Nodes (6): Interface that the Agent delegates to., Modify the chat-completion kwargs before the API call., Return (text_content, [parsed_tool_calls])., Build the assistant message to append to history., Build the message that carries a tool result back to the model., ToolCallingStrategy

### Community 8 - "Tool Registry"
Cohesion: 0.22
Nodes (4): Tool Registry (Chapter 4)  Register tools, expose OpenAI-compatible schemas, dis, Return OpenAI-compatible tool schemas., ToolEntry, ToolRegistry

### Community 9 - "Skills Manager"
Cohesion: 0.22
Nodes (7): Skill Manager (Chapter 10-12)  skill_manage tool: create, patch, edit, delete. s, List all skills with metadata (progressive disclosure tier 1)., Load full skill content (progressive disclosure tier 2-3)., Manage skills: create, edit, patch, delete, write_file, remove_file., skill_manage(), skill_view(), skills_list()

### Community 10 - "CLI & Prompt Builder"
Cohesion: 0.29
Nodes (5): main(), Input function that handles encoding errors gracefully., safe_input(), PromptBuilder, Prompt Builder (Chapter 5)  Assembles the system prompt from identity + memory +

### Community 11 - "Session Recall"
Cohesion: 0.32
Nodes (3): Cross-Session Recall (Chapter 9)  FTS5 search -> group by session -> summarize v, Search past sessions and return summarized context., SessionRecall

### Community 12 - "Prompt Caching"
Cohesion: 0.4
Nodes (5): apply_prompt_caching(), _mark_message(), Prompt Caching (Chapter 6)  system_and_3 strategy: cache the system prompt + las, Apply system_and_3 caching: system prompt + last 3 messages.      Returns a deep, Add cache_control to a message, handling string and list content.

### Community 13 - "File Tools"
Cohesion: 0.33
Nodes (5): File tools (Chapter 4)  Read and write files., Read a file and return its contents., Write content to a file, creating directories as needed., read_file(), write_file()

### Community 14 - "Memory Tool"
Cohesion: 0.4
Nodes (3): memory(), Memory tool (Chapter 8)  Exposes persistent memory to the agent as a callable to, Unified memory tool: save, read, search.

### Community 15 - "Terminal Tool"
Cohesion: 0.5
Nodes (3): Terminal tool (Chapter 4)  Execute shell commands with timeout and output trunca, Execute a shell command and return stdout + stderr., run_terminal()

## Knowledge Gaps
- **68 isolated node(s):** `Mini-Hermes Agent (Chapters 3, 6, 13, 14)  Core agent loop with: - Tool calling`, `Core agent loop: message -> tools -> response.`, `Set the ContextCompressor (Chapter 14).`, `Enable prompt caching (Chapter 6). Only useful for Anthropic models.`, `Run the agent loop for a single user turn. Returns final text.` (+63 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **1 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `main()` connect `CLI & Prompt Builder` to `Tool Calling Strategies`, `Core Agent`, `Persistent Memory`, `Session Database`, `Context Compression`, `Skill Loader`, `Session Recall`?**
  _High betweenness centrality (0.347) - this node is a cross-community bridge._
- **Why does `Agent` connect `Core Agent` to `Tool Calling Strategies`, `CLI & Prompt Builder`, `Tool Calling Base`?**
  _High betweenness centrality (0.216) - this node is a cross-community bridge._
- **Why does `ToolCallingStrategy` connect `Tool Calling Base` to `Tool Calling Strategies`, `Core Agent`?**
  _High betweenness centrality (0.106) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `Agent` (e.g. with `ToolCallingStrategy` and `main()`) actually correct?**
  _`Agent` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 2 inferred relationships involving `SessionDB` (e.g. with `SessionRecall` and `main()`) actually correct?**
  _`SessionDB` has 2 INFERRED edges - model-reasoned connections that need verification._
- **Are the 8 inferred relationships involving `main()` (e.g. with `SessionDB` and `PersistentMemory`) actually correct?**
  _`main()` has 8 INFERRED edges - model-reasoned connections that need verification._
- **What connects `Mini-Hermes Agent (Chapters 3, 6, 13, 14)  Core agent loop with: - Tool calling`, `Core agent loop: message -> tools -> response.`, `Set the ContextCompressor (Chapter 14).` to the rest of the system?**
  _68 weakly-connected nodes found - possible documentation gaps or missing edges._