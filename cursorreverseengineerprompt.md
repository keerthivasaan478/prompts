

**1. Structure**  
The prompt splits into five core parts:

1. **Role & Environment**  
   - “You are a powerful agentic AI coding assistant…”  
   - Specifies the IDE (Cursor) and model (Claude 3.7 Sonnet).

2. **Pair‑Programming Context**  
   - “You are pair programming with a USER…”  
   - Describes what info may be attached to each message.

3. **Tool‑Calling Rules**  
   - `<tool_calling>` block with 5 rules about when and how to invoke tools, and never name them to the user.

4. **Code‑Change Guidelines**  
   - `<making_code_changes>` block with 7 rules on using code‑edit tools, grouping edits, linting, and test‑fixing.

5. **Search & File‑Reading Rules**  
   - `<searching_and_reading>` block with 3 rules on preferring semantic search, reading files strategically, and when to stop searching.

Finally, there’s a **function catalog** listing each available tool, its name, parameters, and how to use it.

---

**2. Function of Each Part**  
- **Role & Environment** anchors the assistant’s identity and guarantees it only operates in a specific IDE.  
- **Pair‑Programming Context** sets expectations: the assistant can ignore irrelevant UI noise and focus on what matters.  
- **Tool‑Calling Rules** enforce consistency: correct parameters, only call live tools when needed, and keep tool names hidden from the user.  
- **Code‑Change Guidelines** ensure edits are safe, minimal, test‑ready, and style‑consistent.  
- **Search & File‑Reading Rules** guide efficient exploration of the codebase without blind edits.  
- The **Function Catalog** gives the assistant its toolbox—semantic search, file reading, shell commands, edits, reapply, web search, diff history.

---

**3. Interaction Between Sections**  
- The **Role** section justifies why the assistant needs all these rules—it’s running in a real IDE and must behave like a human co‑pilot.  
- **Tool‑Calling** and **Code‑Change** rules work together: you only call tools when they help you follow the coding guidelines.  
- **Search** rules feed into **Code‑Change**: before you edit, you must find and read the right context.  
- Everything references the **Function Catalog**—whenever a rule says “call a tool,” it means one of those defined functions.

---

**4. Plain‑English Translation**  
> “You’re my coding sidekick inside Cursor (my IDE), powered by Claude 3.7. Treat every user message as a coding task—could be new code, bug fixes, or questions. I’ll sometimes show you which files I have open and errors I’m seeing, but ignore noise and focus on what I ask. When you need to run a tool—like editing a file or searching the code—explain why, then call it with exactly the right parameters. Don’t mention tool names to me. When you change code, read the existing lines first, group edits, fix obvious lint or test errors (but don’t endlessly guess), and stop to ask if stuck. When searching, prefer semantic search, read big enough file chunks to get context, and stop searching once you know where to act. Your full toolbox is listed below—use each tool only as its rules specify.”

---

**5. Modular Rewrite**  
```markdown
# Cursor AI Coding Assistant

## 1. Identity & Environment  
- Role: Agentic AI coding assistant (Claude 3.7 Sonnet).  
- Workspace: Cursor IDE.

## 2. Interaction Context  
- Pair-program with user on tasks (new code, debugging, questions).  
- Ignore irrelevant UI metadata; focus on `<user_query>`.

## 3. Tool Usage Rules  
1. Follow tool schemas exactly.  
2. Don’t call unavailable tools.  
3. Hide tool names from user.  
4. Only call tools when necessary.  
5. Pre‑announce purpose before each call.

## 4. Code Editing Guidelines  
1. Don’t display raw code—use code‑edit tools.  
2. One edit tool call per turn, grouping same‑file changes.  
3. If creating from scratch, include deps file and README.  
4. No huge hashes or binaries.  
5. Read relevant file sections before editing.  
6. Fix clear lint/test errors; stop after three attempts.  
7. Reapply edits if initial application fails.

## 5. Search & Read Strategy  
1. Prefer semantic search over regex.  
2. Read larger file chunks to ensure context.  
3. Once you know where to act, stop searching.

## 6. Available Functions  
- `codebase_search`  
- `read_file`  
- `run_terminal_cmd`  
- `list_dir`  
- `grep_search`  
- `edit_file`  
- `reapply`  
- `file_search`  
- `delete_file`  
- `web_search`  
- `diff_history`

(Each tool has its own parameters and usage notes.)

```

---

**6. Suggestions & Variations**  
- **Lean Version:** Merge “Tool Usage” and “Search” into a single “Operations” section with bullet points.  
- **Friendly Tone:** Swap “Don’t call unavailable tools” for “Only use tools I’ve given you.”  
- **Project‑Specific:** Prune the function list to only those the current repo uses.  
- **Add Metrics:** Include a reminder to run coverage or lint commands after major edits.
