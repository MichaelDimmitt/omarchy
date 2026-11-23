omarchy keyboard navigation with no mouse - personal cheat sheet

# Omarchy (Hyprland) Computer

Snapshot from Omarchy 4.5.0, 2026-11-22. `super` is the Windows/Omarchy key.
Live sources, in case this file goes stale:
* `super k` or `omarchy menu keybindings --print` - every Hyprland binding
* `super alt k` or `omarchy-menu-tmux-keybindings --print` - tmux
* `super ctrl k` or `omarchy-menu-herdr-keybindings --print` - herdr
* Defaults live in `/usr/share/omarchy/default/hypr/bindings/*.lua`. Personal overrides go in `~/.config/hypr/bindings.lua` (`o.bind`, `o.rebind`, `hl.unbind`). That file has none right now.

## system commands
* menus and help<br/>
`super space` - omarchy menu (launch anything, settings, install)<br/>
`super alt space` - apps launcher<br/>
`super k` - search all keybindings<br/>
`super escape` - system menu (lock, suspend, restart, shutdown)<br/>
`super ctrl o` - toggle menu<br/>
`super ctrl h` - hardware menu<br/>
`super ctrl c` - capture menu<br/>
`super ctrl s` - share menu<br/>
`super ctrl l` - lock system<br/>
`super ctrl i` - toggle lock on idle<br/>

* launch apps<br/>
`super return` - terminal (foot)<br/>
`super alt return` - terminal in tmux<br/>
`super ctrl return` - terminal in herdr<br/>
`super shift return` or `super shift b` - browser (chromium)<br/>
`super shift alt b` - browser private window<br/>
`super shift f` - file manager (nautilus)<br/>
`super shift alt f` - file manager in current directory<br/>
`super shift n` - editor (nvim)<br/>
`super shift o` - obsidian<br/>
`super shift w` - omawrite<br/>
`super shift t` - activity (btop)<br/>
`super shift q` - calculator<br/>
`super shift slash` - passwords<br/>
`super shift m` - music, `super shift alt m` - music TUI<br/>
`super shift ctrl a` - agent<br/>

* web apps<br/>
`super shift a` - chatgpt, `super shift alt a` - grok<br/>
`super shift e` - email, `super shift alt e` - new email<br/>
`super shift c` - calendar<br/>
`super shift g` - signal, `super shift alt g` - whatsapp, `super shift ctrl g` - google messages<br/>
`super shift p` - google photos<br/>
`super shift s` - google maps<br/>
`super shift y` - youtube<br/>
`super shift x` - x, `super shift alt x` - new x post<br/>
`shift alt l` - copy url from a web app<br/>
`shift alt d` - download video from a web app<br/>

* universal clipboard (works in terminals too)<br/>
`super c` - copy<br/>
`super v` - paste<br/>
`super x` - cut<br/>
`super a` - select all<br/>
`super ctrl v` - clipboard history manager<br/>
`super ctrl e` - emoji picker<br/>

* windows<br/>
`super w` or `super q` - close window<br/>
`ctrl alt delete` - close all windows<br/>
`super f` - full screen<br/>
`super ctrl f` - tiled full screen (keeps the bar)<br/>
`super alt f` - full width<br/>
`super t` - toggle floating / tiling<br/>
`super o` - pop window out (float and pin on top)<br/>
`super j` - toggle split direction<br/>
`super p` - pseudo tile<br/>
`super m` - minimize to the dock<br/>
`super backspace` - toggle transparency on a window<br/>
`super ctrl backspace` - toggle single-window square aspect<br/>
`super shift backspace` - toggle window gaps<br/>
`super home` - restore window width, `super alt home` - save window width<br/>
`super left mouse drag` - move window, `super right mouse drag` - resize window<br/>

* focus and move windows<br/>
`super arrow` - focus window in that direction<br/>
`super shift arrow` - swap window in that direction<br/>
`alt tab` / `shift alt tab` - next / previous window (also brings it to the top)<br/>
`ctrl alt tab` / `shift ctrl alt tab` - next / previous monitor<br/>
`super shift ctrl arrow` - move window to monitor in that direction<br/>

* resize windows<br/>
`super minus` - grow left (`alt` = a little, `ctrl` = a lot)<br/>
`super equal` - shrink left (`alt` = a little, `ctrl` = a lot)<br/>
`super shift equal` - grow down (`alt` = a little, `ctrl` = a lot)<br/>
`super shift minus` - shrink up (`alt` = a little, `ctrl` = a lot)<br/>

* workspaces<br/>
`super 1..9, 0` - switch to workspace 1..10<br/>
`super shift 1..9, 0` - move window to workspace and follow it<br/>
`super shift alt 1..9, 0` - move window to workspace silently (stay here)<br/>
`super tab` / `super shift tab` - next / previous workspace<br/>
`super ctrl tab` - former workspace (back and forth)<br/>
`super scroll` - scroll through workspaces<br/>
`super l` / `super alt l` - cycle workspace layout forward / back<br/>
`super shift alt arrow` - move whole workspace to monitor in that direction<br/>

* scratchpad and quake console<br/>
`super s` - toggle scratchpad, `super alt s` - send window to scratchpad<br/>
`` super ` `` - toggle quake drop-down console, `` super shift ` `` - send window to it<br/>

* window groups (tabbed stacks)<br/>
`super g` - toggle grouping<br/>
`super alt arrow` - move window into group in that direction<br/>
`super alt g` - move window out of group<br/>
`super alt 1..5` - switch to window n in group<br/>
`super alt tab` / `super shift alt tab` - next / previous window in group<br/>
`super ctrl left` / `super ctrl right` - move focus within group<br/>
`super alt scroll` - cycle windows in group<br/>

* screenshots, recording, ocr<br/>
`print` or `super ctrl alt c` - screenshot<br/>
`alt print` - screen recording<br/>
`super ctrl print` - extract text (ocr) from a screenshot<br/>
`super print` - color picker<br/>
`super alt [` / `super alt ]` - webcam overlay smaller / larger<br/>

* notifications<br/>
`super comma` - dismiss<br/>
`super alt comma` - dismiss last<br/>
`super shift comma` - dismiss all<br/>
`super shift alt comma` - notification history<br/>
`super ctrl comma` - control notifications with the keyboard<br/>
`super ctrl alt comma` - toggle do not disturb<br/>

* bar and status panels<br/>
`super shift space` - toggle top bar<br/>
`super ctrl 1..9` - open bar panel n<br/>
`super ctrl a` - audio, `super ctrl b` - bluetooth, `super ctrl n` - network<br/>
`super ctrl d` - display, `super ctrl p` - power<br/>
`super ctrl alt t` - show time, `super ctrl alt d` - calendar, `super ctrl alt e` - world clock<br/>
`super ctrl alt b` - battery remaining, `super ctrl alt w` - toggle weather<br/>
`super ctrl r` - set reminder, `super ctrl alt r` - show reminders, `super shift ctrl r` - clear reminders<br/>
`super ctrl period` - transcode<br/>

* themes and look<br/>
`super ctrl t` or `super shift ctrl space` - theme menu<br/>
`super ctrl space` or `super ctrl w` - background switcher<br/>
`super ctrl alt f` - toggle full screen desktop<br/>

* display<br/>
`super slash` / `super alt slash` - monitor scaling up / down<br/>
`super ctrl z` - zoom in, `super ctrl alt z` - reset zoom<br/>
`super ctrl delete` - toggle laptop display<br/>
`super ctrl alt delete` - toggle laptop display mirroring<br/>

* keyboard language and dictation<br/>
`super i` / `super shift i` - switch input method forward / back (fcitx5)<br/>
`left alt + right alt` - switch layout us → dk → eu (your `grp:alts_toggle`)<br/>
`hold alt + right alt` - push-to-talk dictation (start on press, stop on release)<br/>
`alt space` - toggle dictation<br/>
`ctrl alt space` - superwhisper toggle, `escape` - superwhisper cancel<br/>
`shift caps lock` - compose key (see compose section)<br/>

* media and hardware keys<br/>
`volume keys` - volume (`alt` = precise steps), `mute` - mute, `shift mute` - switch audio output<br/>
`mic mute` - mute microphone<br/>
`play` - play/pause, `alt play` / `shift alt play` - next / previous track, `shift play` - switch media source<br/>
`brightness keys` - brightness (`alt` = precise, `shift` = min/max, `ctrl` = keyboard backlight)<br/>
`power key` - power menu<br/>

* text cursor - emacs standard (bash readline, omarchy inputrc)<br/>
`ctrl a` - go to beginning<br/>
`ctrl e` - go to end<br/>
`ctrl k` - delete text after cursor<br/>
`ctrl u` - delete text before cursor<br/>
`ctrl w` - delete word before cursor<br/>
`ctrl -` - undo last text update<br/>
`ctrl r` - backward history search. repeat `ctrl r` to progress. `ctrl g` or `right arrow` to get out of it.<br/>
`up` / `down` - history search matching what you've already typed (omarchy override)<br/>
`tab` / `shift tab` - cycle completions forward / back (menu-complete)<br/>

## terminal commands (foot)
`ctrl shift c` - copy (or `super c`)<br/>
`ctrl shift v` - paste (or `super v`)<br/>
`ctrl shift r` - search scrollback<br/>
`ctrl +` / `ctrl -` / `ctrl 0` - font bigger / smaller / reset<br/>
`shift page up` / `shift page down` - scroll<br/>
`ctrl shift n` - new terminal window in same directory<br/>
`ctrl shift o` - url mode (pick a link with the keyboard)<br/>
`ctrl shift u` - unicode input<br/>

## tmux commands
`super alt return` - open a terminal in tmux<br/>
`ctrl space` - leader (`ctrl b` also works)<br/>
`<leader> ?` - show tmux keybindings<br/>
`<leader> q` - reload config<br/>

* panes (no leader needed)<br/>
`alt return` - split vertically (`<leader> h`)<br/>
`alt shift return` - split horizontally (`<leader> v`)<br/>
`alt escape` - kill pane (`<leader> x`)<br/>
`ctrl alt arrow` - focus pane in that direction<br/>
`ctrl alt shift arrow` - resize pane<br/>
`<leader> z` - zoom pane (tmux default)<br/>

* windows<br/>
`<leader> c` - create window<br/>
`<leader> r` - rename window<br/>
`<leader> k` - kill window<br/>
`alt 1..9` - switch to window n<br/>
`alt left` / `alt right` - previous / next window<br/>
`alt shift left` / `alt shift right` - move window left / right<br/>

* sessions<br/>
`<leader> C` - create session<br/>
`<leader> R` - rename session<br/>
`<leader> K` - kill session<br/>
`<leader> P` / `<leader> N` or `alt up` / `alt down` - previous / next session<br/>
`<leader> s` - session picker (tmux default)<br/>
`<leader> d` - detach (tmux default)<br/>

* copy mode (vi keys)<br/>
`<leader> [` - enter copy mode<br/>
`v` - begin selection<br/>
`y` - copy selection and exit<br/>

## herdr commands
`super ctrl return` - open a terminal in herdr<br/>
`ctrl space` - leader<br/>
`<leader> ?` - help, `<leader> s` - settings, `<leader> q` - reload config, `<leader> d` - detach<br/>

* workspaces<br/>
`<leader> w` - workspace picker, `<leader> g` - goto<br/>
`<leader> C` - new workspace, `<leader> G` - new git worktree<br/>
`<leader> R` - rename workspace, `<leader> K` - close workspace<br/>
`alt up` / `alt down` - previous / next workspace<br/>

* tabs<br/>
`<leader> c` - new tab, `<leader> r` - rename tab, `<leader> k` - close tab<br/>
`alt left` / `alt right` - previous / next tab<br/>
`alt shift left` / `alt shift right` - move tab<br/>
`alt 1..9` - switch to tab n<br/>

* panes<br/>
`alt return` - split horizontal, `alt shift return` - split vertical<br/>
`alt escape` - close pane<br/>
`ctrl alt arrow` - focus pane, `ctrl alt shift arrow` - resize pane<br/>
`<leader> tab` / `<leader> shift tab` - cycle panes, `<leader> ;` - last pane<br/>
`<leader> z` - zoom, `<leader> b` - toggle sidebar<br/>
`<leader> e` - edit scrollback, `<leader> [` - copy mode<br/>
`ctrl v` - paste image to a remote session<br/>

## vim commands
`super shift n` - open nvim (LazyVim, via omarchy-nvim)<br/>
`space` - leader. Press it and wait for which-key to list everything.<br/>
6 modes of vim: https://www.geeksforgeeks.org/the-six-modes-of-vim-editor
#### LazyVim essentials
1. `space space` - find files
2. `space /` - grep across the project
3. `space e` - file explorer
4. `space ,` - switch buffer
5. `space g g` - lazygit
6. `space c a` - code action, `g d` - go to definition, `K` - hover docs
7. `space q q` - quit all
#### navigating in normal mode
1. gg - navigate to top
2. shift + g - navigate to bottom
3. 0 - beginning of line
4. $ - end of line
#### switch to insert mode from normal mode
1. shift i - enter insert mode and move cursor to beginning of line
2. shift a - enter insert mode and move cursor to end of line
3. esc - move from insert mode back to normal mode.
#### other normal mode commands
1. `esc :` - for entering vim commands.
2. `esc :wq` - escape write and quit
3. ctrl v - enter visual block mode

## compose key (shift caps lock, then type the sequence)
`compose m s` 😄, `m c` 😂, `m l` 😍, `m h` ❤️, `m y` 👍, `m n` 👎, `m p` 🙏, `m o` 👌, `m x` 🎉, `m 1` 💯<br/>
`compose space space` - em dash —<br/>
`compose space n` / `compose space e` - your name / email. Both are blank in `~/.XCompose`, so fill them in.<br/>
Full list: `/usr/share/omarchy/default/xcompose`

## gotchas found on this machine
1) **The `¨michael` typo:** `~/.config/hypr/input.lua` sets `kb_variant = "intl"`. On US-international, `"` and `'` are dead keys, so `"` then `m` typed `¨m`. To get a plain quote, press `"` then `space`. To stop it, drop `kb_variant`.
2) **Overloaded alt keys:** `left alt + right alt` switches keyboard layout (us/dk/eu), and holding `alt + right alt` also starts push-to-talk dictation. Pressing both Alts may do both.
3) **`super c` / `super v` vs `ctrl c`:** use `super c` / `super v` everywhere, including terminals. In a terminal, `ctrl c` still sends interrupt.
4) **`ctrl space` is the leader in both tmux and herdr.** Running one inside the other means the outer one catches the leader, so press it twice (or use `ctrl b` for tmux). Omarchy binds `ctrl space` to "direct input" so fcitx5 passes it through to the terminal and doesn't eat it.

## questions remaining for me to add to
1) chromium shortcuts on linux (mostly mac `command` → `ctrl`)
2) vscode / cursor, if installed later
