---
layout: default
title: Gangs
parent: Scripts
has_children: true
nav_order: 4
---

# 🏴 EM Studios Gangs
{: .no_toc }

A modular and immersive gang territory system for RedM built for VORP. Includes infamy, territory control, tax banking, crafting, and promotion systems.

---

## 📑 Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 🔧 Requirements

- [VORP Core](https://github.com/VORPCORE/vorp_core-lua)
- MySQL (via ghmattimysql or oxmysql)
- RedM (FXServer)

---

## 📦 Installation

1. Download and unzip this resource into your server's `resources` folder.
2. Add it to your `server.cfg`:

```cfg
ensure EM_Studios_Gangs
```

3. Import the provided SQL files (`gangs`, `gang_members`, `gang_infamy`, `zone_balances`).
4. Configure your zones and crafting stations in `config.lua`.
5. (Optional) Set up Discord webhooks and role synchronization.

---

## ⚙️ Configuration

You can configure nearly every aspect of this script using `config.lua`.

### 🔐 Gang Creation

```lua
Config.UseGangPermit = true         -- Require item to create a gang
Config.GangPermitItem = "gang_permit"
Config.PermitAmount = 1
```

### 🧾 Infamy Settings

```lua
Config.InfamyPerTick = 10                  -- Passive infamy gain from KOTH
Config.InfamyLossPerKill = 5              -- Infamy loss when peds are killed
Config.ReduceInfamyOnKill = true
Config.AllowNonGangInfamyLoss = false
```

### 🗺️ Zone Mapping

```lua
Config.ZoneHashToName = {
    [459833523] = "Valentine",
    [2046780049] = "Rhodes",
    ...
}
```

### 🛠️ Crafting & Purchasables

Define recipes and purchasables per zone in the `Config.CraftingStations` table.

```lua
Config.CraftingStations["Valentine"] = {
  recipes = {
    {
      label = "Molotov",
      ingredients = {
        { item = "alcohol", count = 1 },
        { item = "cloth", count = 1 }
      },
      reward = { item = "molotov", count = 1, label = "Molotov Cocktail" },
      craftTime = 3000
    }
  }
}
```

---

## 🔁 Exports

See [Gang Exports](./gang-exports.md) for full integration documentation.


---

## 🖼️ UI Showcase

- ✅ EM Studios-style dark NUI
- ✅ Gang list, invites, and ranks
- ✅ Infamy values and zone control indicators
- ✅ Dynamic crafting and territory earnings

---

## 📬 Support

Join our Discord for support, bug reports, or suggestions:  
[https://discord.gg/pugmjxBKR8](https://discord.gg/pugmjxBKR8)

---

## 📄 License

MIT License — see `LICENSE` file for details.

