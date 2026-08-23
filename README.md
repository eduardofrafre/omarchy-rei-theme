# Rei

![Rei theme preview](preview.png)

## Inspiration

Named after and inspired by **Rei Ayanami** from *Neon Genesis Evangelion* —
her signature light blue hair and eyes are the seed for this palette. The
theme leans on a single muted blue (`#617bb9`) as the accent across the
terminal, window borders, and UI, echoing her cold, quiet color scheme
against a near-black background.

## Install

```bash
omarchy theme install https://github.com/dufrtss/rei-omarchy-theme
```

This gives you the color palette, icon theme, wallpaper, and a gradient
window-border color driven straight from `colors.toml` (see below).

## Matching the border style and window transparency

The screenshot's transparent, thin, gradient window borders and the
slightly see-through terminal/editor come from two places: one is baked
into this theme, the other is a personal Hyprland preference you'll need to
add yourself.

**Already included when you install this theme** — the border gradient
(transparent → `#617bb9` at ~70% opacity, 45°) is defined in `colors.toml`
via Omarchy's `hyprland_active_border` / `hyprland_inactive_border` keys,
and applies automatically to window borders (`general.col`) and window
group/tab borders (`group.col`):

```toml
hyprland_active_border = "rgba(617bb900) rgba(617bb9b3) 45deg"
hyprland_inactive_border = "rgba(617bb955)"
```

**Not part of the theme (add to your own `~/.config/hypr/` files)** —
border thickness isn't a theme color, so it lives in your personal
`~/.config/hypr/looknfeel.lua`:

```lua
hl.config({
  general = {
    border_size = 1,
  },
})
```

And the slight transparency on terminals and VS Code is a personal window
rule in `~/.config/hypr/hyprland.lua`:

```lua
-- Slight transparency for terminals and the IDE (active/inactive opacity).
o.window({ tag = "terminal" }, { opacity = "0.90 0.85" })
o.window("^(code)$", { opacity = "0.90 0.85" })
```

After editing either file, Hyprland picks up the change on save — run
`hyprctl reload` to force it, and `hyprctl configerrors` to confirm there
are no typos.
