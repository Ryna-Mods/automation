# Automation by Ryna

A mod of [Ryna](https://github.com/Ryna-Mods/ryna) for World of Warcraft: Forever. Does the chores you tick: quests, vendors, trainers, mail, loot rolls, invites, resurrections, dialogs
and cinematics.

- **Each chore is a tick box** on an Automation tab in Ryna's settings, and each starts off.
- **Nothing happens until you turn it on.** Hold Shift to pause it; it pauses itself in combat.
- `/ryna auto` shows what is on.

It acts in the game for you, which is why it is off until you ask. It needs nothing from the Ryna app
and sends nothing anywhere.

## Installing

Automation needs **Ryna Core** (the folder `Ryna_Core`). Get both one of these ways:

- **With the Ryna app** ([download](https://github.com/MaddisonM79/ryna_agent/releases/latest)),
  which installs them and keeps them up to date.
- **The bundle**: every Ryna addon in one zip, from
  [Ryna-Mods/ryna](https://github.com/Ryna-Mods/ryna/releases/latest).
- **By hand**: this repository's releases hold `Ryna_Automation-<version>.zip`; unzip it into
  `Interface/AddOns` beside `Ryna_Core`.

## Working on it

`Ryna_Automation/` is the addon. Its tests (`test/`) run it against a fake client and the real core
addon, the oldest one Automation claims to work with ([`core.json`](core.json)), which
`node scripts/core.mjs` fetches into `.core/`.

```bash
scripts/check.sh
```

That is everything CI runs: luacheck, the strings (`tools/strings.mjs`: every string the code uses
is in `Locales/enUS.lua` and in each locale's template) and the tests. It needs Lua (5.1 is what the
game runs), [luacheck](https://github.com/lunarmodules/luacheck) and Node.

The core API level Automation needs is `## X-Ryna-API` in [`Ryna_Automation.toc`](Ryna_Automation/Ryna_Automation.toc);
its version is `## Version` there, and nowhere else. A release is a signed tag `vX.Y.Z` that matches
it; the bundle then names that release in its `bundle.json`
([how](https://github.com/Ryna-Mods/ryna/blob/main/RELEASING.md)).

## Where it came from

Automation was written in [MaddisonM79/ryna_agent](https://github.com/MaddisonM79/ryna_agent)
(`mods/wow/automation`), and its history up to 0.5.0 is there. Bugs and requests go to
[ryna_agent's issues](https://github.com/MaddisonM79/ryna_agent/issues).

## Licence

MIT.
