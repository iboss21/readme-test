TLE AI Revive — ambient rescue spawns + contract board + first-aid + carry & deliver to medic + rewards, with big config and multi-framework adapters (RSG/LXR/QBR/VORP/Standalone).

What’s inside
[TheLuxEmpire]/[Services]/tle_ai_revive/
fxmanifest.lua # lua54 + escrow_ignore (config/locales/media)
config.lua # huge, editable config (items, timers, spawns, boards, rewards)
locales/
en.lua
ka.lua
shared/
utils.lua # locale helpers, fade, rand, debug
client/
streaming.lua # model/anim loaders
prompts.lua # prompt helpers
scene.lua # spawn downed NPCs, revive scene, carry & delivery radius
missions.lua # mission board UI (simple) + contract start feedback
server/
framework.lua # money/items/notify stubs for RSG/LXR/QBR/VORP (+standalone)
rewards.lua # payouts, rep, cooldowns
missions.lua # world ambient spawns, contract acceptance, revive handling
README_TEBEX.md # Keymaster → Tebex publishing steps
LISTING.md # ready-to-paste product description
CHANGELOG.md
LICENSE # MIT
media/
cover.png # promo cover (store)
banner.png # category/banner image
Features (quick)
Ambient signals: periodic injured NPC spawns (weighted archetypes with different causes/severity).

First aid: item-gated, fade-to-black mini scene with configurable time and failure chance.

Carry & Deliver: attach/carry stabilized NPC to a medic zone → cash reward + rep.

Mission Boards: pick contracts with time limits (lost traveler/trapper/wagon accident), per-board configs.

Reputation (Compassion) + decay; cooldowns; anti-abuse (no loot during rescue).

Framework adapters: RSG/LXR/QBR/VORP money & items are stubbed to slots you can map to your exact APIs.
