# DockLabels Changelog

---

## 0.9.2 07 May 2026

### Performance & Memory
- **Fixed massive memory leak** — NSVisualEffectView `.behindWindow` removed, replaced with lightweight semi-transparent CALayer backgrounds
- **CF memory leaks fixed** — AXUIElementCopyAttributeValue retain counts now properly consumed via `takeRetainedValue()`
- **CGFontStrike / layer backing store explosion eliminated** — font sizes now rounded to 0.5-step increments during Dock zoom instead of generating 8,400+ unique sizes in 30 seconds
- Polling reduced from 144Hz to 60Hz
- Title/text caching at 5-second intervals, instant refresh on settings change

### Visual
- **Labels now have semi-transparent backgrounds** — clean look, theme-aware (light/dark)
- Font size slider updates labels in real-time during drag (no more waiting for slider to stop)
- Vertical offset slider: instant visual feedback

### Fixes
- CFArray leak in `getDockIconsCached()` — called at 60Hz, was leaking a CFArray every tick
- Settings refresh gated on window visibility (was refreshing while hidden)
- Dock position detection cached for 5s to reduce AX overhead

---

## 0.9.1 19 April 2026

### Licensing & Backend
- **Gumroad Integration** - License keys verified against Gumroad API
- **Device Limit** - 3 devices per license
- **WAF Rate Limiting** - Cloudflare WAF handles rate limiting (2 req/10s per IP)

### App Changes
- **Trial Mode** - 14-day free trial with modeless activation window when expired
- **Soft Hyphen Fix** - German "Systemeinstellungen" now correctly shortens to "Einstell." (handles U+00AD soft hyphen)
- **Settings UI** - "Deactivate and Quit" button, improved layout with bugs/feedback row
- **Unified Short Names** - 84 redundant entries removed from dictionary (where long name = short name)
- **Added More Languages** - to handle short mode

### Build System
- **Dual Architecture Scripts** - Separate builds for Intel (x86_64) and Apple Silicon (arm64)
- **Notarized Builds** - Both architectures signed with Developer ID and notarized

---
