# 🛠️ Master Antigravity Multi-Agent Construction Protocol (GitClaw)

## 1. System Mission
This repository houses the dedicated **30-Agent Multi-Division Engineering Organization** designed to build, test, audit, and package **GitClaw** (the autonomous AI Git & GitHub CLI).

---

## 2. Construction DAG Relay Architecture

```text
[Phase 1: Architecture & Git Plumbing]
01_chief_architect ──> 02_git_plumbing_engineer ──> 03_reflog_specialist ──> 04_ast_merge_engineer
                                         │
                                         ▼
[Phase 2: Core Go Systems & CLI]
05_cobra_cli_lead ──> 06_go_concurrency_lead ──> 07_worktree_sandbox_lead ──> 08_compiler_specialist
                                         │
                                         ▼
[Phase 3: Integration & UX]
09_github_auth_lead ──> 10_ci_log_parser ──> 11_pr_lifecycle_lead ──> 12_review_comment_resolver
13_ollama_local_specialist ──> 14_cloud_llm_router ──> 15_prompt_minifier
16_repo_dna_indexer ──> 17_fix_pattern_curator ──> 18_maintainer_rules_engine
19_bubbletea_architect ──> 20_lipgloss_designer ──> 21_diff_viewer_engineer
                                         │
                                         ▼
[Phase 4: Security & TDD Verification]
22_secret_shield_auditor ──> 23_shell_injection_guard ──> 24_prompt_injection_guard
25_synthetic_repo_gen ──> 26_tdd_unit_test_lead ──> 27_e2e_integration_lead
                                         │
                                         ▼
[Phase 5: Multi-Model Review Council (Concurrent)]
28_code_reviewer + 29_backward_compat_guard
                                         │
                                         ▼
[Phase 6: Release & Distribution]
30_goreleaser_lead (Multi-OS Binary Packaging)
```

---

## 3. Mandatory Construction Standards
- **Language:** Go 1.22+ (Single static binary, <15MB, zero external runtime dependencies).
- **Test-First Discipline:** Every package (`pkg/git`, `pkg/github`, `pkg/ai`, `pkg/memory`, `pkg/sandbox`) must have table-driven unit tests verified against synthetic repos.
- **Local-First Privacy:** Default to local Ollama (`qwen2.5-coder:7b`) with zero telemetry.
- **Secret Shield:** Intercept all credentials before committing or pushing.
