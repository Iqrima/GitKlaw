# 🦀 GitClaw

> **The Autonomous Local-First Git Co-Pilot & Disaster Recovery Engine.**  
> *Never lose a commit, botch a rebase, or ship buggy PRs again. Powered by 100% offline Local AI (Ollama) or Cloud LLMs.*

---

[![License: MIT](https://img.shields.io/badge/License-MIT-emerald.svg)](LICENSE)
[![Go Version](https://img.shields.io/badge/Go-1.22+-blue.svg)](https://golang.org)
[![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-blueviolet.svg)](https://github.com)
[![Local AI](https://img.shields.io/badge/Local%20AI-Ollama%20(100%25%20Offline)-success.svg)](https://ollama.ai)
[![Security](https://img.shields.io/badge/Security-Zero%20Data%20Egress-brightgreen.svg)](docs/security.md)

---

## 💡 The Big Problem with Git Today

Every single software engineer knows these three terrifying moments:

1. **The 3:00 PM Git Disaster**: You ran `git reset --hard` or `git rebase -i` on the wrong branch. Days of uncommitted code or stashed work vanished into the void of the reflog.
2. **The 5-Way Merge Conflict**: 47 files are in conflict. `<<<<<<< HEAD` markers everywhere. One wrong click breaks the entire build.
3. **The Expensive Cloud Code Review**: Tools like CodeRabbit and Copilot require you to send private, proprietary source code to third-party cloud servers, costing thousands of dollars per seat while risking confidential IP.

```
                   THE DEVELOPER NIGHTMARE
                   
    ❌ Lost Commits         ❌ Botched Rebase        ❌ Leaked Code & IP
    "Where is my code?"     "Merge conflicts!"      "$20/user/mo cloud SaaS"
             \                      |                      /
              \                     |                     /
               ▼                    ▼                    ▼
       ┌─────────────────────────────────────────────────────────┐
       │                       GITCLAW                           │
       │     The 100% Local Autonomous Git Rescue Engine         │
       └─────────────────────────────────────────────────────────┘
                                    │
                                    ▼
       ✅ 1-Click Reflog Rescue     ✅ AST Conflict Solver    ✅ 100% Offline AI
```

---

## ⚡ What is GitClaw?

**GitClaw** is a lightweight, single-binary CLI & interactive Terminal UI (TUI) written in Go. It acts as an autonomous Git engineer sitting right in your terminal:

* **🚑 Instant Disaster Recovery**: Visualizes dangling blobs and detached HEAD commits in an interactive time-machine DAG, resurrecting lost code in 1 click.
* **🧠 AST-Aware Merge & Conflict Resolver**: Resolves complex Git conflicts by understanding programming language syntax trees rather than simple text line diffs.
* **🔒 100% Private, Offline AI Reviews**: Reviews your local branch or pull request using your local Ollama models (`qwen2.5-coder`, `deepseek-r1`, `llama3`) with **zero bytes leaving your machine**.
* **✨ CI Failure Sentry**: Directly ingests broken GitHub Actions/GitLab CI logs, isolates the failing unit test, and applies the patch in a sandboxed worktree.

---

## 🚀 How GitClaw Works

```mermaid
flowchart TD
    subgraph LocalDev["💻 Your Local Machine (100% Offline)"]
        User["Developer / Terminal"]
        CLI["🦀 GitClaw CLI & TUI\n(Charm Bubbletea)"]
        GitCore["Git Invariant Engine\n(Reflog & Worktree Sandbox)"]
        LocalLLM["🦙 Ollama Local AI\n(Qwen2.5 / DeepSeek-R1)"]
        MemoryVault["🧠 3-Tier Memory Vault\n(Repo DNA & Past Fixes)"]
    end

    subgraph Remote["🌐 Optional Cloud & Remotes"]
        GitHub["GitHub / GitLab PRs"]
        CloudLLM["Claude 3.7 / OpenAI\n(Optional Fallback)"]
    end

    User <-->|Interactive TUI / CLI| CLI
    CLI <--> GitCore
    CLI <-->|Local Inference (Zero Egress)| LocalLLM
    CLI <-->|Continuous Learning| MemoryVault
    CLI -.->|Optional PR Sync| GitHub
    CLI -.->|Optional Cloud Power| CloudLLM
```

---

## 🛠️ Key Capabilities

### 1. 🛟 `gitclaw rescue` — Undo the "Un-undoable"
Accidentally ran `git reset --hard`? Lost a detached HEAD?
```bash
gitclaw rescue
```
GitClaw scans your reflog, object store, and dangling blobs, reconstructs the timeline in a beautiful terminal tree, and lets you preview and restore lost snapshots safely.

```
┌───────────────────────── 🦀 GitClaw Rescue Time-Machine ─────────────────────────┐
│                                                                                   │
│  [2 mins ago]  HEAD@{1}  commit (reset)  feat: auth token refresh (LOST)  ◄ RESTORE │
│  [15 mins ago] HEAD@{2}  rebase -i       checkout target/main                     │
│  [1 hour ago]  HEAD@{3}  commit          refactor: database connection pool       │
│                                                                                   │
│  Diff Preview for Lost Commit [a4f19b2]:                                          │
│  + func RefreshAuthToken(ctx context.Context, token string) (*Token, error) {    │
│  +     return authProvider.Exchange(ctx, token)                                   │
│  + }                                                                              │
│                                                                                   │
│  [Enter] Restore to branch 'rescue/auth-token'   [Esc] Cancel                     │
└───────────────────────────────────────────────────────────────────────────────────┘
```

---

### 2. 🧩 `gitclaw resolve` — AST-Level Conflict Auto-Fixer
Traditional Git treats merge conflicts as dumb text. GitClaw parses language Abstract Syntax Trees (AST) to resolve conflicts logically:
```bash
gitclaw resolve --auto
```
* Merges non-conflicting functions automatically even if they share line numbers.
* Sorts and deduplicates imports and dependencies without human intervention.
* Tests the resolved code inside an isolated Git worktree before committing.

---

### 3. 🔍 `gitclaw review` — Private, Fast PR & Local Branch Audits
Get deep, senior-level code reviews directly in your terminal before pushing to GitHub:
```bash
# Review local uncommitted diff offline with local Ollama
gitclaw review --local

# Review remote GitHub PR #42 with inline suggestions
gitclaw review pr 42
```
* Catches subtle concurrency bugs, memory leaks, missing error checks, and SQL injections.
* Zero cloud dependencies when using `--model=ollama:qwen2.5-coder`.

---

### 4. 🧠 `gitclaw learn` — The 3-Tier Persistent Memory Vault
GitClaw gets smarter the more your team uses it. Stored locally in `.agents/memory/`:
* **Repo DNA**: Adapts to your repository's naming styles, error handling conventions, and test setups.
* **Fix Patterns**: Remembers how you resolved past merge conflicts and CI failures.
* **Maintainer Rules**: Enforces custom team guidelines during reviews.

---

## 📊 GitClaw vs. The Competition

| Feature | 🦀 GitClaw | CodeRabbit | GitHub Copilot | GitLens |
| :--- | :---: | :---: | :---: | :---: |
| **100% Offline / Local AI (Ollama)** | ✅ **Yes** | ❌ No | ❌ No | ❌ No |
| **Zero Code/Data Egress Guarantee** | ✅ **Yes** | ❌ No | ❌ No | ⚠️ Partial |
| **Reflog Disaster Recovery Engine** | ✅ **Yes** | ❌ No | ❌ No | ⚠️ View only |
| **AST-Aware Merge Conflict Auto-Fix** | ✅ **Yes** | ❌ No | ❌ No | ❌ No |
| **Autonomous Sandboxed CI Repair** | ✅ **Yes** | ❌ No | ❌ No | ❌ No |
| **Self-Learning Repo Memory Vault** | ✅ **Yes** | ⚠️ Cloud-only | ❌ No | ❌ No |
| **Pricing** | 🆓 **Open Source** | 💸 \$15–\$24/mo/user | 💸 \$10–\$19/mo/user | 💸 \$9–\$14/mo |

---

## ⚡ Quick Start

### Installation

```bash
# Via Homebrew (macOS/Linux)
brew install gitclaw/tap/gitclaw

# Via Go install
go install github.com/gitclaw/gitclaw@latest

# Via Direct Binary (Windows/Linux/macOS)
curl -fsSL https://gitclaw.dev/install.sh | bash
```

### 30-Second Setup

```bash
# 1. Initialize GitClaw in your repo
gitclaw init

# 2. Check repo health & Git tree status
gitclaw status

# 3. Run a quick review using your local Ollama
gitclaw review --model ollama:qwen2.5-coder
```

---

## 🏗️ Architecture & Philosophy

GitClaw is built with four uncompromising core engineering principles:

1. **Safety First (Zero Workspace Dirt)**: All exploratory operations, AST merges, and dry-runs happen in disposable `.git/worktrees/` scratchpads. Your working tree is never touched unless a fix is 100% verified.
2. **Local-First, Cloud-Optional**: Full power with Ollama and local heuristics. Connect to Claude or OpenAI only when you explicitly configure API keys.
3. **Unix Philosophy**: Fast startup (<15ms), pipeable output formats (`json`, `diff`, `interactive`), and zero heavy runtime dependencies (single static binary).
4. **Secret Shield**: Integrated pre-scan engine scrubs tokens, private keys, and environment secrets before feeding context to any LLM.

---

## 🤝 Community & Roadmap

* [x] **v0.1**: Git Reflog Disaster Recovery & Rescue TUI
* [x] **v0.2**: AST Merge Conflict Resolver for Go, TypeScript, Rust, Python
* [ ] **v0.3**: Local Ollama DeepSeek-R1 Streamlined Code Reviews
* [ ] **v0.4**: CI Failure Auto-Healer & GitHub PR In-line Fix Decorator
* [ ] **v1.0**: Multi-Repo Organization Memory & Team Knowledge Sync

---

<p align="center">
  <b>Built for developers who value speed, privacy, and their sanity.</b><br>
  <sub>Licensed under the MIT License • Contributions Welcome</sub>
</p>
