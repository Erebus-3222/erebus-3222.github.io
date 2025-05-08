---
layout: default
title: Gang Exports
parent: Gangs
---


# 📘 EM_Studios_Gangs Exports
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

These exports allow your other RedM scripts to interact with the gang system – including gang infamy, zone control, and tax earnings.

---

## Requirements

- [ ] [VORP](https://github.com/VORPCORE/vorp_core-lua)

---

## Notes

🛈 Some exports use `:next(function(result) ... end)` — this means they return a **promise**. You must handle the response using the callback pattern shown in the examples.

🛈 `zoneName` can be a **string** (e.g. `"Valentine"`) or a **zone hash** (e.g. `459833523`) — both are supported.

---

### ✅ `AddGangInfamy`

Use this when a gang gains influence by action (e.g., mission success). Rivals in the same zone lose infamy.

```lua
exports["EM_Studios_Gangs"]:AddGangInfamy(charId, zoneName, amount)
```

**Arguments:**
- `charId` *(number)* — Character ID (from `getUsedCharacter.charIdentifier`)
- `zoneName` *(string or number)* — Zone name or zone hash
- `amount` *(number)* — Infamy amount to add (max 1000)

**Notes:**
- Rival gangs **lose the same amount** of infamy.
- Caps at 1000 infamy.

<details>
<summary>Example</summary>

```lua
exports["EM_Studios_Gangs"]:AddGangInfamy(12345, "Valentine", 50)
```
</details>

---

### ✅ `AddPlayerGangInfamy`

Adds infamy to the gang of a given player without affecting rivals.

```lua
exports["EM_Studios_Gangs"]:AddPlayerGangInfamy(source, zoneName, amount):next(function(success) ... end)
```

**Arguments:**
- `source` *(number)* — Player’s server ID
- `zoneName` *(string or number)* — Zone name or hash
- `amount` *(number)* — Infamy to add

**Returns:** `true` or `false`

<details>
<summary>Example</summary>

```lua
exports["EM_Studios_Gangs"]:AddPlayerGangInfamy(source, "Rhodes", 25):next(function(success)
    if success then
        print("Infamy granted!")
    end
end)
```
</details>

---

### ✅ `SubtractPlayerGangInfamy`

Subtracts infamy from the player’s gang in a specific zone.

```lua
exports["EM_Studios_Gangs"]:SubtractPlayerGangInfamy(source, zoneName, amount):next(function(success) ... end)
```

**Arguments:**
- `source` *(number)* — Player’s server ID
- `zoneName` *(string or number)* — Zone name or hash
- `amount` *(number)* — Infamy to subtract

**Returns:** `true` or `false`

---

### ✅ `IsPlayerInGang`

Checks whether a player is currently in any gang.

```lua
exports["EM_Studios_Gangs"]:IsPlayerInGang(source):next(function(isInGang) ... end)
```

**Arguments:**
- `source` *(number)* — Player’s server ID

**Returns:** `true` or `false`

---

### ✅ `DoesGangControlZone`

Checks if a gang **controls** a zone (requires 500+ infamy and no other gang with same score).

```lua
exports["EM_Studios_Gangs"]:DoesGangControlZone(gangName, zoneName):next(function(result) ... end)
```

**Arguments:**
- `gangName` *(string)* — Name of the gang
- `zoneName` *(string or number)* — Zone name or hash

**Returns:** `true` or `false`

---

### ✅ `GetPlayerGangZoneControlLevel`

Returns how much control the player's gang has over a zone.

```lua
exports["EM_Studios_Gangs"]:GetPlayerGangZoneControlLevel(source, zoneName):next(function(level) ... end)
```

**Arguments:**
- `source` *(number)* — Player’s server ID
- `zoneName` *(string or number)* — Zone name or hash

**Returns:**
- `"none"` — Player’s gang has no control
- `"partial"` — 500+ infamy but under 1000
- `"full"` — 1000 infamy (full control)

---

### ✅ `WithdrawZoneBalance`

Lets a gang owner claim the tax balance from a controlled territory.

```lua
exports["EM_Studios_Gangs"]:WithdrawZoneBalance(source, zoneName):next(function(success) ... end)
```

**Arguments:**
- `source` *(number)* — Player’s server ID
- `zoneName` *(string or number)* — Zone name or hash

**Returns:** `true` or `false`

**Requirements:**
- Player must be **gang owner**
- Their gang must control the zone

---

### ✅ `PayTaxToControllingGang`

Deposits tax earnings into the gang bank of the **controlling gang** in a zone.

```lua
exports["EM_Studios_Gangs"]:PayTaxToControllingGang(zoneName, amount, source):next(function(success) ... end)
```

**Arguments:**
- `zoneName` *(string or number)* — Zone name or hash
- `amount` *(number)* — Amount to deposit
- `source` *(number, optional)* — Server ID of the player paying the tax

**Returns:** `true` or `false`

**Notes:**
- Only works if a gang controls the zone (500+ infamy and no tie)
- Sends right-tip notification if `source` is provided

---

### ✅ `GetGangByCharId`

Fetches a character's gang name using their ID.

```lua
exports["EM_Studios_Gangs"]:GetGangByCharId(charId, function(gangName) ... end)
```

**Arguments:**
- `charId` *(number)* — Character ID (from `getUsedCharacter.charIdentifier`)
- `function(gangName)` — Callback receives the gang name (or `nil` if none)

---

## ✅ Valid Zones

You can use these zone names (or their hashes) with any export:

- `"Valentine"`
- `"Rhodes"`
- `"Saint Denis"`
- `"Blackwater"`
- `"Tumbleweed"`
- `"Strawberry"`
- `"Annesburg"`
- `"Van Horn"`
- `"Armadillo"`
- `"Lagras"`

---
