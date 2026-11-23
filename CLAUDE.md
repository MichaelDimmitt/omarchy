# CLAUDE.md

Notes repo for this Omarchy machine. This repo is **public**, so never commit secrets,
tokens, personal config contents beyond `~/.config/hypr/{input,bindings}.lua`, or anything from `~/.XCompose`.

## "refresh" / "bring this up to date"

1. Run `bin/refresh`. It's read-only, so it never runs sudo or installs anything.
2. Run `git diff --stat snapshots/`, then read the diff of each changed file.
3. Update the curated docs with only what changed. The README table "If this snapshot changed… → update this" says which section goes with which snapshot:
   - `situational-awareness.md`: bump the snapshot date, the versions, the pending-update list and the missing/extra tables. When a problem in §3 is resolved, mark it ✅ with the date; don't delete it.
   - `keybindings.md`: add, change or remove bindings to match `snapshots/keybindings-*.txt`. Keep the existing format: `* group<br/>` headers, then `` `keys` - description<br/> `` lines, lowercase key names, `super` = Omarchy key. Fold repetitive bindings (1..9, resize steps) into one line.
4. Commit with a message that summarizes what changed (e.g. "Refresh: omarchy 4.6, 3 new bindings"), then push.

## Gotchas

- Don't run `npm`, `node`, `uv` or any other lazily-installed mise tool just to inspect it. Running it downloads it. Use `mise ls` instead.
- `omarchy update` needs sudo and an interactive confirmation. Ask the user to run it in a real terminal. Don't run it in the background.
- Missing pacman sync DBs make every package look "foreign". `bin/refresh` checks against the `checkupdates` temp DB instead.
- Editing `~/.config/hypr/*`: back the file up first, then run `hyprctl reload && hyprctl configerrors`. Keymap changes also need `omarchy restart xcompose` (fcitx5).
