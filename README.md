# omarchy

Personal notes on my [Omarchy](https://omarchy.org/) laptop: what Omarchy ships by default, what's
different on this machine, and the keybindings I need to work without a mouse.

| File | What it is |
|---|---|
| [`situational-awareness.md`](situational-awareness.md) | Omarchy's default packages and mise tools, how this machine differs, pending updates, things missing |
| [`keybindings.md`](keybindings.md) | Cheat sheet: Hyprland, foot, tmux, herdr, nvim, readline, compose key, plus gotchas found here |
| [`snapshots/`](snapshots/) | Raw output captured from the machine by `bin/refresh`. Don't edit by hand |
| [`bin/refresh`](bin/refresh) | Regenerates `snapshots/`. Read-only: no sudo, no installs |

Machine: AMD Ryzen AI 7 350 / Radeon 860M · Omarchy 4.5 · `linux-omarchy` kernel. See [`snapshots/meta.txt`](snapshots/meta.txt) for current values.

## Bringing it up to date

```bash
cd ~/Work/omarchy
bin/refresh                    # ~2 seconds, rewrites snapshots/
git diff --stat snapshots/     # what moved since the last refresh
git diff snapshots/            # the actual changes
```

Then fold anything meaningful into the two docs and commit:

| If this snapshot changed… | …update this |
|---|---|
| `meta.txt` (Omarchy version, sync DBs, last `-Syu`) | header of `situational-awareness.md` |
| `packages-diff.txt` (extra, missing or orphaned packages) | §2 of `situational-awareness.md` |
| `updates.txt` (pending pacman, AUR or mise updates) | §3 of `situational-awareness.md` |
| `mise-installed.txt`, `mise-lazy.txt` | §1c and §2 mise table |
| `keybindings-*.txt` | matching section of `keybindings.md` |
| `hypr-overrides.txt` (my changes to the hypr templates) | "gotchas" in `keybindings.md` |

You can also open Claude Code in this folder and say **"refresh"**. [`CLAUDE.md`](CLAUDE.md) tells it
how to run the script, read the diff, update the docs and commit.

## Typical maintenance loop

```bash
omarchy update                 # apply system, AUR and mise updates (needs sudo, run in a real terminal)
bin/refresh && git diff --stat snapshots/
git add -A && git commit -m "Refresh snapshots" && git push
```

## Where the truth lives on the machine

- Default packages: `/usr/share/omarchy/install/omarchy-*.packages` (`omarchy-pkg-defaults` prints the list for this platform)
- Default mise tools: `/etc/mise/conf.d/omarchy-tools.toml`
- Default Hyprland bindings: `/usr/share/omarchy/default/hypr/bindings/*.lua`. Mine go in `~/.config/hypr/bindings.lua`
- Live keybinding lists: `super k`, `super alt k` (tmux), `super ctrl k` (herdr)
