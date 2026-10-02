# AI Bridge

Shared coordination space for Dwayne Crump's AI assistants: Claude, ChatGPT, Grok, Gemini.

## For AIs reading this: how it works

1. **This file is your orientation.** Read it first.
2. **Each project has its own folder** under `/projects/<slug>/`. Inside:
   - `context.md` — background on the project. Read once per session.
   - `current-task.md` — what Dwayne needs *right now*. Read every turn.
   - `log.md` — append-only chat history across all AIs. Read for the latest state.
3. **If `current-task.md` says "WAIT FOR DIRECTION", do not act.** Reply to Dwayne saying you've read the bridge and are standing by. Do not propose work, do not run tools, do not generate content until he gives you direction here or in chat.
4. **If you contribute**, append your turn to `log.md` with a header like `## 2026-10-02 05:30 - <your name>` so humans and other AIs can trace who did what.
5. **Claude Code (the terminal CLI) is the orchestrator.** It writes `current-task.md` based on Dwayne's direction. Other AIs read and respond.

## Raw URLs to feed each AI

For a given project `<slug>`, point the other AI at these:

- Context: `https://raw.githubusercontent.com/GhettoMediaGroup/ai-bridge/main/projects/<slug>/context.md`
- Current task: `https://raw.githubusercontent.com/GhettoMediaGroup/ai-bridge/main/projects/<slug>/current-task.md`
- Log: `https://raw.githubusercontent.com/GhettoMediaGroup/ai-bridge/main/projects/<slug>/log.md`

## Current projects

- [presidential-black-car](projects/presidential-black-car/current-task.md)

## How to submit back (V1 - manual)

Right now the write path is manual. Workflow:

1. Dwayne tells an AI (Grok/GPT/Gemini): "Read `<raw URL to current-task.md>`."
2. The AI reads it and replies to Dwayne in its own chat.
3. **If the AI has something to log back to the bridge**, it should wrap its response in a block like this:

   ````
   ```bridge-submit
   project: presidential-black-car
   ai: grok|gpt|gemini
   message: <your contribution here>
   ```
   ````

4. Dwayne pastes that block into Claude Code or opens an Issue on this repo, and Claude Code commits it to the right `log.md`.

**V2 (planned):** a public form at `bridge.ghettomediagroup.com` that each AI can tell Dwayne to paste into. Submission hits a Cloudflare Worker that commits the entry directly. See the `webhook` branch when it exists.
