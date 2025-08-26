# TLE Companions (RedM)

**Companions/Escorts & Saloon Services** for RedM. Non-explicit, RP-friendly, fade-to-black cinematics, and flexible pricing.  

Multi-framework support: **RSG**, **LXR**, **QBR**, **VORP**, or **Standalone** (auto-detect).

- Paid services: Dance, Warm Bath, Private Room (PG-13)

- Huge, editable config (spawners, prices, law/witness, buffs, reputation, cooldowns)

- Smart NPC spawning and prompt UI

- Best‑effort framework adapters (money/notify/hooks)

## Install

1. Place the folder in `resources/[TheLuxEmpire]/[Services]/tle_companions`

2. Add to `server.cfg`:

   ```

   ensure tle_companions

   ```

3. Configure `config.lua` (locale, prices, spawners, framework mode if desired).



## Notes

- **No explicit content**. Visuals rely on dance/bath anims or fade‑to‑black.

- Money removal and law hooks are adapter‑based. Adjust the calls in `server/framework.lua` to match your exact core versions if needed.

- `escrow_ignore` exposes `config.lua` and `locales/` for buyers.



## Credits

- iBoss · The Lux Empire



# TLE Companions — Tebex/Keymaster Packaging



This package is prepared for **Cfx.re escrow** and Tebex distribution.



## Editable (NOT encrypted)

- `config.lua`

- `locales/*.lua`

- `media/*` (images/banners)



These are declared in `fxmanifest.lua` under `escrow_ignore`.



## How to publish on Keymaster + Tebex

1. **Zip the resource folder** so the zip **root** contains `fxmanifest.lua` (already done in this package).

2. Go to **Keymaster → Assets** and create a new asset. Upload this zip to produce an escrowed build.

3. In **Tebex Creator** dashboard, create a product and attach the generated **Keymaster asset** as the deliverable.

4. Add your listing copy and screenshots (`media/`) on the product page.



## Notes

- This resource is **client+server Lua** only; no DB migrations required.

- Works with **RSG / LXR / QBR / VORP** or **Standalone** (auto-detect; can force via `Config.Framework`).

- If your framework uses different money/notify APIs, edit `server/framework.lua` (clearly marked stubs).
