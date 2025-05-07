---
layout: default
title: Gang Exports
parent: Scripts
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

### ✅ `AddGangInfamy`

```lua
exports["EM_Studios_Gangs"]:AddGangInfamy(charId, zoneName, amount)
```

Adds infamy to the gang of the character ID. Rival gangs lose an equal amount of infamy in the same zone.

**Arguments:**
- `charId` *(number)* — Character identifier (from `getUsedCharacter.charIdentifier`)
- `zoneName` *(string)* — Name of the zone (e.g., `"Valentine"`)
- `amount` *(number)* — Amount of infamy to add (maximum is 1000)

**Note:** Rival gangs in the same zone will lose `amount` infamy as well.

---

### ✅ `AddPlayerGangInfamy`

```lua
exports["EM_Studios_Gangs"]:AddPlayerGangInfamy(source, zoneName, amount):next(function(success) ... end)
```

Adds infamy to the gang of the specified player. **Does not affect** rival gangs.

**Arguments:**
- `source` *(number)* — Server ID of the player
- `zoneName` *(string)* — Zone to increase infamy in
- `amount` *(number)* — Infamy amount to add

**Returns:** `true` if success, `false` otherwise

---

### ✅ `SubtractPlayerGangInfamy`

```lua
exports["EM_Studios_Gangs"]:SubtractPlayerGangInfamy(source, zoneName, amount):next(function(success) ... end)
```

Removes infamy from the player’s gang in a specific zone.

**Arguments:**
- `source` *(number)* — Server ID of the player
- `zoneName` *(string)* — Zone to subtract infamy from
- `amount` *(number)* — Infamy amount to subtract

**Returns:** `true` if success, `false` otherwise

---

### ✅ `IsPlayerInGang`

```lua
exports["EM_Studios_Gangs"]:IsPlayerInGang(source):next(function(isInGang) ... end)
```

Checks if the player is currently in a gang.

**Arguments:**
- `source` *(number)* — Server ID of the player

**Returns:** `true` or `false`

---

### ✅ `DoesGangControlZone`

```lua
exports["EM_Studios_Gangs"]:DoesGangControlZone(gangName, zoneName):next(function(result) ... end)
```

Checks if a gang controls a territory (requires 500+ infamy and no other gang tied).

**Arguments:**
- `gangName` *(string)* — Name of the gang to check
- `zoneName` *(string)* — Name of the zone

**Returns:** `true` if gang controls the zone, `false` otherwise

---

### ✅ `GetPlayerGangZoneControlLevel`

```lua
exports["EM_Studios_Gangs"]:GetPlayerGangZoneControlLevel(source, zoneName):next(function(level) ... end)
```

Returns the level of control the player’s gang has over the specified zone.

**Arguments:**
- `source` *(number)* — Server ID of the player
- `zoneName` *(string)* — Zone to check control over

**Returns:** One of the following strings:
- `"none"` — No control
- `"partial"` — 500+ infamy, but not full control
- `"full"` — 1000 infamy (maximum)

---

### ✅ `WithdrawZoneBalance`

```lua
exports["EM_Studios_Gangs"]:WithdrawZoneBalance(source, zoneName):next(function(success) ... end)
```

Withdraws tax money from a controlled zone. Only works if the player is the **gang owner** and their gang **controls** the zone.

**Arguments:**
- `source` *(number)* — Server ID of the player
- `zoneName` *(string)* — Zone to withdraw from

**Returns:** `true` if the withdrawal was successful, `false` if not

---

### ✅ `PayTaxToControllingGang`

```lua
exports["EM_Studios_Gangs"]:PayTaxToControllingGang(zoneName, amount, source):next(function(success) ... end)
```

Pays money into the tax bank of the gang that controls the specified zone.

**Arguments:**
- `zoneName` *(string)* — Zone name (e.g., `"Rhodes"`)
- `amount` *(number)* — Amount of money to deposit
- `source` *(number)* — (Optional) Server ID of the player paying the tax. Will receive a right-tip notification.

**Returns:** `true` if the zone is controlled and payment was successful, `false` otherwise

---

### ✅ `GetGangByCharId`

```lua
exports["EM_Studios_Gangs"]:GetGangByCharId(charId, function(gangName) ... end)
```

Fetches the gang name a character belongs to.

**Arguments:**
- `charId` *(number)* — Character identifier
- `function(gangName)` — Callback function that receives the gang name or `nil` if not in one

**Returns:** Nothing directly (async callback)
