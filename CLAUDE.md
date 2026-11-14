# Development Protocol — Do Not Deviate

## Feature Development Workflow

1. **Simulation first**: All new features or UI changes must be built as an artifact/simulation for the user to review and approve functionality before any code is written.
2. **Dev build second**: Only after explicit user approval of the simulation: build the feature into `index-dev.html`.
3. **User tests dev**: User tests `index-dev.html` on their device before anything goes live.
4. **Live push last**: Only after user says "push live": copy `index-dev.html` → `index.html`, bump `sw.js` cache version (e.g. `marathon-v7` → `marathon-v8`), commit both, then tell user to run `git push`. Never run `git push` directly.

## Hard Rules

- **Never modify `index.html` directly** — it is the live production file.
- **Never modify `sw.js`** until the live push step.
- **Never run `git push`** from Claude's environment.
- **Never copy `index-dev.html` to `index.html`** until user explicitly says "push live".
- **Never delete Firebase run logs** for user "Toddrick".
- **Never display or decode the embedded API key** (stored as base64 in the app).

## Git Commit Convention

End every commit message with:
```
Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>
Claude-Session: https://claude.ai/code/session_01KufKQhxMVLm2vSdewGPg27
```

After each commit, rename any HEAD.lock left behind:
```
mv .git/HEAD.lock .git/HEAD.lock.stale
```
