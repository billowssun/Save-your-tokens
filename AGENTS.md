# Global Codex Cost-Saving Rules

These instructions apply across Codex workspaces unless a project-level `AGENTS.md` gives more specific guidance.

## Command Execution

- Prefer the smallest useful command before broad inspection.
- Keep exploration scoped to the user's current goal.
- Do not read large logs, full dependency trees, or full files unless necessary.
- When command output is long, inspect only the relevant tail or error section.
- Avoid repeated status checks unless the previous result is ambiguous.
- Do not fix unrelated issues unless the user explicitly asks.

## GitHub And Git

- Before committing, use minimal checks:
  - `git status --short`
  - targeted diff for files being committed
  - build or test only when requested or necessary
- Avoid broad history inspection unless the task depends on history.
- Do not inspect CI, create PRs, or check deployments unless requested.
- If a push fails, inspect the shortest useful error output first.
- Summarize Git state in chat instead of dumping full command output.

## Vercel

- Do not deploy unless deployment is explicitly requested.
- Prefer local build validation before remote Vercel checks.
- When inspecting deployments, read only the final status and relevant error lines.
- Avoid repeated polling of deployment status unless monitoring is requested.

## NPM And Builds

- On Windows, prefer `cmd /c npm.cmd ...` if PowerShell blocks `npm`.
- Avoid reinstalling dependencies if `node_modules` already exists and the task does not require dependency changes.
- For build failures, inspect the first actionable error and final summary instead of full logs.

## Communication

- Before expensive or networked operations, state the intended command group.
- Ask before full CI inspection, production deploys, repeated remote checks, or broad repo scans.
- When skipping an expensive check, say exactly what was skipped and why.
