# TAMIDS AI Jumpstart: Vibe Coding

Use **Claude Code** with your **TAMU AI Chat** account (daily budget $10.0).

This repository contains the setup instructions for the TAMIDS AI Jumpstart vibe coding session. By pointing Claude Code at the Texas A&M AI Chat API endpoint, you can run Claude Code inside VS Code without an Anthropic subscription and without logging in.

> **Who this is for:** Texas A&M students, faculty, and staff with a NetID. TAMU AI Chat is available only to A&M employees and students.

---

## What you will end up with

| Piece | Purpose |
| --- | --- |
| VS Code | The editor where you will work |
| Claude Code extension | The AI coding agent |
| `~/.claude/settings.json` | Tells Claude Code to send requests to TAMU AI Chat instead of Anthropic |
| TAMU AI Chat API key | Your credential (treat it like a password) |

Estimated setup time: 10 to 15 minutes.

---

## Step 0. Get your TAMU AI Chat API key

1. Go to [https://tamu.ai/](https://tamu.ai/) and log in with your NetID.
2. Click your avatar (top right), then **Settings** → **Account** → **API keys**.
3. Create a key and copy it. It looks like `sk-...`.
4. Keep it somewhere handy for Step 4. **NEVER share it with others or post it online.**

Documentation for TAMU AI Chat, including the API docs, lives at [https://docs.tamus.ai/](https://docs.tamus.ai/).

<!-- ![Where to find your API key](figures/step0-api-key.png) -->

---

## Step 1. Install VS Code

Download and install Visual Studio Code: [https://code.visualstudio.com/](https://code.visualstudio.com/)

<!-- ![VS Code download page](figures/step1-vscode.png) -->

---

## Step 2. Install the Claude Code extension

In VS Code, open the Extensions panel (`Ctrl + Shift + X` on Windows, `Cmd + Shift + X` on Mac), search for **Claude Code**, and install it.

Installing first means the `~/.claude/` folder and a starter `settings.json` will already exist when you get to the next step.

<!-- ![Claude Code extension in the marketplace](figures/step2-extension.png) -->

---

## Step 3. Open your Claude Code settings file

Open the VS Code terminal (`Ctrl + `` ` `` on Windows, `Cmd + `` ` `` on Mac, or **Terminal → New Terminal**), then paste and run:

```bash
code ~/.claude/settings.json
```

This opens `settings.json` as a new tab in VS Code. If the file does not exist yet, VS Code will open an empty tab with that name, which is fine.

<!-- ![settings.json opened in VS Code](figures/step3-settings.png) -->

---

## Step 4. Add the TAMU AI Chat configuration

Add this `env` block to `settings.json`:

```json
"env": {
  "ANTHROPIC_BASE_URL": "https://chat-api.tamu.ai/api",
  "ANTHROPIC_AUTH_TOKEN": "<YOUR TAMU AI CHAT API KEY>",
  "ANTHROPIC_MODEL": "protected.Claude Sonnet 4.6"
},
```

Replace `<YOUR TAMU AI CHAT API KEY>` (including the angle brackets) with the key you copied in Step 0.

**If the file already has content**, scroll to the bottom and insert the block just before the second-to-last line, for example before `"model": "haiku"`. Make sure every entry except the last one ends with a comma.

**If the file is empty**, paste this complete file instead:

```json
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://chat-api.tamu.ai/api",
    "ANTHROPIC_AUTH_TOKEN": "<YOUR TAMU AI CHAT API KEY>",
    "ANTHROPIC_MODEL": "protected.Claude Opus 4.8"
  },
  "model": "haiku"
}
```

<!-- ![Edited settings.json](figures/step4-env-block.png) -->

---

## Step 5. Save

Save the file with `Ctrl + S` (Windows) or `Cmd + S` (Mac).

If VS Code underlines something in red, you most likely have a missing or extra comma. Check that the braces and brackets are balanced.

---

## Step 6. Open Claude Code and start vibe coding

Open the Claude Code extension from the VS Code sidebar (or run **Claude Code: Focus** from the Command Palette). You should be able to start prompting right away, with no login screen.

If Claude Code was already running, quit and reopen VS Code so it picks up the new settings.

<!-- ![Claude Code running in VS Code](figures/step6-claude-code.png) -->

---

## Verify it is working

Type a short prompt in Claude Code, for example:

```
Create a Python script that prints the first 20 Fibonacci numbers, then run it.
```

If you get a response, you are connected.

---

## Troubleshooting

| Symptom | Likely cause and fix |
| --- | --- |
| Claude Code asks you to log in | The `env` block is not being read. Confirm the file is at `~/.claude/settings.json`, that it saved, and restart VS Code. |
| `401` or authentication error | The API key is wrong, expired, or the angle brackets were left in. Generate a new key at [tamu.ai](https://tamu.ai/) and paste it again. |
| `404` or model not found | The model name changed. Log in to TAMU AI Chat and check the exact model ID, then update `ANTHROPIC_MODEL`. |
| Requests suddenly stop working | You may have hit your daily token limit. Limits reset between 6 and 7 p.m. Central Time. |
| `code` is not recognized in the terminal | Open the Command Palette in VS Code and run **Shell Command: Install 'code' command in PATH**, then reopen the terminal. |
| Red squiggles in `settings.json` | JSON syntax error, usually a comma. |

---

## Important reminders

- **Your API key is a credential.** Do not commit `settings.json` to a public repository, do not paste your key into a shared document, and do not include it in screenshots.
- **Mind your data classification.** TAMU AI Chat supports content classified as University-Confidential or lower. Do not use it for data that exceeds that classification.
- **Model availability changes.** Model names and the list of available models are set by the TAMU AI Chat service and may be updated over time.

---

## Resources

- TAMU AI Chat: [https://tamu.ai/](https://tamu.ai/)
- TAMU AI Chat documentation: [https://docs.tamus.ai/](https://docs.tamus.ai/)
- Texas A&M AI services overview: [https://www.it.tamu.edu/ai-services/](https://www.it.tamu.edu/ai-services/)
- VS Code: [https://code.visualstudio.com/](https://code.visualstudio.com/)
- Original setup gists: [Step 3](https://gist.github.com/CandiceChuDVM/448c7207130e83737363691c8f22d03f), [Step 5](https://gist.github.com/CandiceChuDVM/c93927fa1dd43be6a478e408d2887013)

---

*Prepared for the TAMIDS AI Jumpstart vibe coding session.*
