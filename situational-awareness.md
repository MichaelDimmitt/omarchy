# Situational Awareness: Omarchy on this machine

Snapshot taken **2026-11-22**.

| | |
|---|---|
| Omarchy | `omarchy 4.5.0-3`, installed 2026-11-04 |
| Kernel | `linux-omarchy 7.2.15-1` (BORE CPU scheduler, ADIOS I/O scheduler) |
| Platform | `x86` (per `omarchy-hw-platform`) |
| Computer | **Framework Laptop 13 Pro**. Firmware reports `Framework Laptop 13 (AMD Ryzen AI 300 Series)`, board revision A7, SKU `FRANWCCP07` |
| BIOS | INSYDE `04.02` (2026-06-09) |
| CPU | AMD Ryzen AI 7 350, 8 cores / 16 threads |
| GPU | Radeon 860M integrated (Krackan), driver `vulkan-radeon` |
| Memory | 32 GB RAM, plus 30.6 GB zram swap |
| Storage | 2 TB WD_BLACK SN7100 NVMe (btrfs + snapper) |
| Display | built-in 13.5" 2880×1920 @ 120 Hz (3:2), Hyprland scale 1.6 |
| Wireless | MediaTek MT7925 (RZ717), Wi-Fi 7 160 MHz + Bluetooth |
| Keyboard | Framework keyboard. `fn esc` toggles Fn lock, and **no light shows its state**: test with the brightness key (see `keybindings.md`) |
| Package managers present | pacman, yay (AUR), mise, plus npm, uv and gem through mise or the system |
| Not present | flatpak, snap, brew, nix, pipx, cargo/rustup, fwupd |

---

## 1. What Omarchy installs by default

As of 4.x, Omarchy ships as an Arch **package** (`omarchy`) from its own repo
(`[omarchy]` at `pkgs.omarchy.org/stable`). It no longer lives in a git checkout at
`~/.local/share/omarchy`. Everything is under `/usr/share/omarchy/`.

The source of truth for the defaults is on disk:

| File | Purpose |
|---|---|
| `/usr/share/omarchy/install/omarchy-base.packages` | ~162 packages installed on every machine |
| `/usr/share/omarchy/install/omarchy-other.packages` | Packages installed some other way: hardware-detected drivers, bootloader, firmware, ISO extras |
| `/usr/share/omarchy/install/omarchy-{aarch64,…}.packages` | Additions for ARM platforms (not used here) |
| `/etc/mise/conf.d/omarchy-tools.toml` | Developer and agent CLIs that mise manages (installed lazily) |
| `/etc/mise/conf.d/omarchy-agent-accounts.toml` | Wrappers that send `claude`, `codex` and `grok` through `omarchy-agent-account-exec` |
| `/etc/mise/conf.d/omarchy.toml` | mise settings (`upgrade.auto_prune = false`, cursor-agent alias) |

`omarchy-pkg-defaults` prints the effective default list for this platform.

### 1a. Pacman packages in `omarchy-base`, grouped

- **Desktop/WM:** hyprland, hyprland-guiutils, hyprland-preview-share-picker, hyprpicker, hyprsunset, quickshell, uwsm, sddm, plymouth, xdg-desktop-portal-{gtk,hyprland}, xdg-terminal-exec, omarchy-hyprland-titlebars, aether (theming)
- **Terminal and CLI:** foot, tmux, starship, bash-completion, bat, eza, fd, fzf, ripgrep, zoxide, jq, gum, btop, fastfetch, less, man-db, tldr, plocate, inxi, lazygit, git, nvim (provided by `neovim`) + omarchy-nvim (LazyVim), tree-sitter-cli, vi, whois, unzip, socat, expac, usage, tobi-try, herdr
- **Dev runtimes and libs:** base-devel, ruby, lua51, luarocks, dotnet-runtime, mariadb-libs, postgresql-libs, libyaml, libvips, python-gobject, python-poetry-core, qt6-* (base, declarative, multimedia, svg, wayland, imageformats), qemu-user-static-binfmt
- **Package and version management:** **mise-bin**, **yay**, pacman-contrib
- **Containers:** docker, docker-buildx, docker-compose, ufw, ufw-docker
- **Apps:** chromium, obsidian, libreoffice-fresh, localsend, mpv (+mpv-mpris), imv, evince, pinta, nautilus (+python, sushi), gnome-disk-utility, moonlight-qt, signed, superwhisper-bin, disktree-bin, cliamp, gliff, owe
- **Omarchy apps:** hype, monologue, omacalc, omacut, omawrite, omasnap, ttfx, omarchy-power-profiles-daemon
- **Media and screen:** ffmpeg, ffmpegthumbnailer, imagemagick, gpu-screen-recorder, grim, slurp, wl-clipboard, wtype, yt-dlp, tesseract (+eng), zbar, qrencode
- **Hardware and system:** bluez (+tools, utils), bolt, brightnessctl, ddcutil, asdcontrol, alsa-utils, pamixer, wireplumber, networkmanager, avahi, nss-mdns, cups (+filters, pk-helper), system-config-printer, gvfs-{mtp,nfs,smb}, udiskie, dosfstools, exfatprogs, kernel-modules-hook, tzupdate, wireless-regdb, inotify-tools, inetutils
- **Input methods:** fcitx5 + chewing, chinese-addons, gtk, hangul, mozc, qt, table-extra
- **Fonts and icons:** noto-fonts (+cjk, emoji), ttf-jetbrains-mono-nerd-basic, ttf-ia-writer, woff2-font-awesome, yaru-icon-theme, gnome-themes-extra
- **Security:** gnome-keyring, libsecret

The `omarchy` package also depends on `omarchy-settings`, `omarchy-keyring`, `omarchy-themes-intros`,
`omarchy-speedtest`, `omarchy-security-functions`, `limine` + `limine-snapper-sync` + `snapper`
(btrfs snapshots), pipewire and perl.

### 1b. Packages from `omarchy-other` installed on this machine

Hardware detection picked these from the "other" list: base, btrfs-progs, limine (+mkinitcpio hook,
snapper-sync), linux-omarchy (+headers), linux-firmware, snapper, sof-firmware, zram-generator,
pipewire (+alsa, jack, pulse), gst-plugin-pipewire, gtk4-layer-shell, libpulse, qt6-wayland,
**vulkan-radeon**, libvpl. No NVIDIA, Intel, Apple T2, Dell or ASUS extras were installed, which is
correct for an AMD laptop.

### 1c. mise: the second package manager

mise is installed as `mise-bin` (pacman) and configured system-wide. Omarchy declares about 31
tools in `/etc/mise/conf.d/omarchy-tools.toml`, all with `version = "latest"` and **`lazy = true`**.
A lazy tool has a shim but isn't downloaded until its first use. Agent CLIs also have
`auto_update = "4h"`.

- **Dev tools:** node, uv, gh, playwright, hunk, ghui, basecamp, hey-cli
- **AI agent CLIs:** claude, codex, copilot, cursor-agent, opencode, crush, amp, grok, qwen, pi, oh-my-pi, muse, ori, antigravity-cli, devin, kiro-cli, kilocode, kimi-code, minimax code, deepseek dsh, command-code, freebuff, cf

User overrides belong in `~/.config/mise/config.toml`. That file does not exist yet.

### 1d. Other Omarchy setup

- `~/Work` and `~/Work/tries` are created at install (`user/mise-work.sh`). Both exist.
- `omarchy update` (alias `omarchy up`) runs pacman `-Syu`, `yay -Sua` (only when foreign
  packages exist), `mise up` with `MISE_MINIMUM_RELEASE_AGE=0`, orphan pruning and keyring updates.
- `omarchy-update-firmware` installs `fwupd` on demand and then runs `fwupdmgr update`.

---

## 2. What's different on this machine (diff from the defaults)

### Pacman: explicitly installed but not in Omarchy's lists

| Package | Why it's here | Verdict |
|---|---|---|
| amd-ucode, intel-ucode | Installer adds both microcode packages | Expected. `intel-ucode` isn't needed on AMD but does no harm |
| efibootmgr, mkinitcpio, sudo, openssh | Base system from the installer | Expected |
| neovim | Provides `nvim` from the base list | Expected |
| omarchy, omarchy-keyring, omarchy-settings | Omarchy itself | Expected |

**Result:** apart from the installer basics, nothing extra was installed with pacman.
There are no AUR or other foreign packages: `pacman -Qqm` against a freshly synced DB
returns nothing. There are no orphans.

### Pacman: in the defaults but missing

`omarchy-pkg-defaults` was checked package by package with `pacman -T`.
**Nothing is missing.** (`nvim` counts as satisfied because `neovim` provides it.)

### Failed install: `claude-desktop`

`/var/log/pacman.log` shows `pacman -S --needed claude-desktop` run twice on 2026-11-13. It is
**not installed**. The package does exist in the `[omarchy]` repo (`6.28899.6-1`). The likely cause
is below: this machine's pacman sync databases are missing, so `pacman -S` (without `-y`) couldn't
find the package.

### mise: user-level state

| Tool | Installed version(s) | Notes |
|---|---|---|
| claude | 2.1.323, **2.1.330** | Updates itself. The old version is kept because Omarchy turns off `auto_prune`. Remove it with `mise prune` |
| gh | 2.104.0 | 2.105.0 is available |
| node | 26.13.1 | Downloaded on 2026-11-22 when this survey ran `npm` |
| uv | 0.13.9 | Downloaded on 2026-11-22 when this survey ran `uv` |
| everything else | not downloaded (lazy) | Downloads on first use. Nothing to do |

- mise itself: **2026.11.0**, while 2026.11.12 is available. It updates through pacman (`mise-bin`), not `mise self-update`.
- npm globals: none besides npm. uv tools: none. gems: only Ruby's default gems.

---

## 3. Health check: updates and anything not installed that should be

### 🔴 Pacman sync databases are missing

```
/var/lib/pacman/sync/  →  only offline.db (from the ISO install, 2026-11-04)
warning: database file for 'core' does not exist (use '-Sy' to download)
```

`pacman` has never synced from the online repos since install. As a result:
- `pacman -Si`, `pacman -Ss` and `pacman -S <pkg>` fail or return nothing. This is what broke `claude-desktop`.
- `pacman -Qm` reports every package as foreign, so `omarchy update` would run `yay -Sua` against the whole system.
- No system package has been updated since install, 18 days ago.

**Fix:** `omarchy update` (runs `pacman -Syu` and the rest of the Omarchy update chain).

### Pending pacman updates (from `checkupdates`, 9 packages)

```
aether             4.32.0-2   -> 4.33.0-1
cliamp             2.3.0-3    -> 2.4.1-1
gliff              0.4.2-1    -> 0.4.3-1
herdr              0.9.1-2    -> 0.9.5-1
mise-bin           2026.11.0-1 -> 2026.11.12-1
omarchy-speedtest  0.2.1-1    -> 0.2.2-1
owe                0.2.13-1   -> 0.2.14-1
superwhisper-bin   1.2.0-1    -> 1.3.1-1
yt-dlp             2026.08.19-1 -> 2026.10.26-1
```

`omarchy` itself (4.5.0) and the kernel are up to date.

### Pending mise updates

- `gh` 2.104.0 → 2.105.0
- `claude`: current. Old 2.1.323 can be pruned.

### Not installed but probably should be

| Item | Recommendation |
|---|---|
| `claude-desktop` | Retry after syncing: `omarchy-pkg-add claude-desktop` (or `sudo pacman -S claude-desktop`) |
| `fwupd` | Optional. Install it via `omarchy-update-firmware` to check BIOS, EC and SSD firmware on this new Ryzen AI laptop |
| `~/.config/mise/config.toml` | Optional. Create it when you want to pin your own tool versions (ruby, python, etc.) |

### Suggested action order

1. `omarchy update`: syncs DBs, applies the 9 pacman updates and `mise up` (gh).
2. `omarchy-pkg-add claude-desktop`.
3. `mise prune`: clears the old claude version.
4. Optional: `omarchy-update-firmware`.
5. Run this survey again to confirm the machine is clean.

---

## Appendix: commands used

```bash
cat /usr/share/omarchy/install/omarchy-base.packages
omarchy-pkg-defaults                                  # effective default list
for p in $(omarchy-pkg-defaults); do pacman -T "$p" >/dev/null || echo "$p"; done
comm -23 <(pacman -Qqe | sort) <(sort omarchy-*.packages)   # extras
checkupdates                                          # pending repo updates, no root needed
pacman -Qqm --dbpath /tmp/checkup-db-$UID             # true foreign/AUR pkgs
pacman -Qdtq                                          # orphans
mise ls ; mise outdated
npm ls -g --depth=0 ; uv tool list ; gem list
```

## Sources

- Local: `/usr/share/omarchy/install/*.packages`, `/etc/mise/conf.d/*.toml`, `/usr/share/omarchy/bin/omarchy-update*`
- [The Omarchy Manual: Other Packages](https://learn.omacom.io/2/the-omarchy-manual/66/other-packages)
- [Omarchy 2.0: Mise for organizing dev environments](https://akitaonrails.com/en/2025/09/07/omarchy-2-0-mise-for-organizing-dev-environments/)
- [omarchy on the AUR](https://aur.archlinux.org/packages/omarchy)
