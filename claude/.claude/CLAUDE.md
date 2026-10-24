## Output

- When pointing to a specific code location, include `path:line:column` with 2–3 lines of surrounding context in a fenced code block. Always read the file first — never rely on prior search output for context lines.

## Writing style

- Use American English for artifacts: code, comments, and docs.
- Do not hard-wrap text bodies (commit messages, Markdown, etc.). Let each paragraph be a single long line. Exception: match existing style in the file or codebase.
- The 100-character line limit applies to code only, not to Markdown or commit messages.
- When opening with a Smart Brevity lede — a short label followed by a colon — capitalize both the label and the first word after it: "Note: Existing callers are unaffected", not "Note: existing callers are unaffected".
- Describe technical behavior literally, as cause and effect. No personification or narrative flourish: "`read` blocks, since the PTY never sends input", not "waits for an answer nobody gives".
- In commit messages, PR descriptions and comments, and Linear issues, write high level and lean on bullets: a framing sentence, then short bullets. Leave out file paths, function names, version detail and test minutiae unless the reader acts on them.

### Vocabulary

- Don't use "would" when describing behavior. Use "can" or "will".
- Avoid the word "actual" unless necessary. Prefer "target", "real", or other more precise terms.
- Use "tradeoff" instead of "trade-off".

## Code style

- You MUST end every file with a single trailing newline, unless an `.editorconfig` says otherwise.
- Use `import type` for type-only imports.
- Do not add `@ts-ignore`, `@ts-expect-error`, or `$FlowFixMe` without a comment explaining why.
- Do not use `any` — prefer `unknown`, proper generics, or a specific type.
- Prefer `test()` over `it()` in tests.
- Use the package manager, linter, formatter and test runner the repo already uses, as its lockfile, config and `package.json` scripts show (expo/expo: pnpm, oxlint, oxfmt). The global JavaScript tooling defaults apply only where a repo sets none, such as a new project.
- When marking code sections, use `// #region` / `// #endregion` pairs. Keep blank lines around the code inside a region, but no blank line between an `#endregion` and the next `#region`.

### Comments and docs

- Comments and docs describe the code as it stands, not how it got there — write for a reader seeing the final result cold. Do not encode the path that produced the code: rejected alternatives, "changed from X to Y", "now uses…", "no longer…", or rationale that only made sense against an earlier draft.
- Keep a "why" comment only when the reason is non-obvious from the code itself and still true of the final version.

### Markdown tables

- **New tables:** Use `---` (no padding) in separator cells; do not align columns.
- **Existing tables:** Preserve column widths and separator style. Only change cell content unless structure is explicitly wrong.

### Swift

- Write doc comments with `///`, not `/** */`.

## Workflow

- Update test snapshots when changes are intentional, and call them out in the summary.

### Commits

- Do not create or amend commits unless explicitly asked.
- Always use the `/commit-msg` skill to generate commit messages.
- When amending a commit, also update the commit message to reflect the new changes.
- Pull requests go to GitHub. Once a PR is open, its description on GitHub is the source of truth for the message body.

### Build & verification

- Run the specific test file you changed with the repo's test runner, not the full suite.
- Run lint and typecheck before considering a task complete.
- Never set `CI` to silence a prompt: tools bundle unrelated behavior behind it, such as Expo, Jest, and Vitest disabling file watching. Redirect instead (`cmd < /dev/null > out.log 2>&1 &`), or use a tool's single-purpose variable (`GH_PROMPT_DISABLED`, `NO_COLOR`, `EXPO_NO_QR_CODE`).
