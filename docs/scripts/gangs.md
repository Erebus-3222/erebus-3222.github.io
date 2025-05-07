---
layout: default
title: Gang Exports
parent: Scripts
---

# Gang Exports
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

This page documents all available exports for the `EM_Studios_Gangs` script, including full usage examples and descriptions.

## Requirements
- [ ] [VORP Core](https://github.com/VORPCORE/vorp_core-lua)
- [ ] MySQL (GHMattiMySQL)
- [ ] Compatible UI (already integrated)

## Exports

---

### `AddGangInfamy`

Adds infamy to a gang by character ID and reduces rival gangs in the same zone.

```lua
exports["EM_Studios_Gangs"]:AddGangInfamy(charId, "Valentine", 100)
```

- `charId`: character ID of the player
- `"Valentine"`: name of the territory
- `100`: amount of infamy to add (max 1000)

---

### `AddPlayerGangInfamy`

Adds infamy to the player's gang **without** affecting rivals.

```lua
exports["EM_Studios_Gangs"]:AddPlayerGangInfamy(source, "Rhodes", 50):next(function(success)
    if success then
        print("Infamy added.")
    end
end)
```

---

### `SubtractPlayerGangInfamy`

Removes infamy from the player's gang only.

```lua
exports["EM_Studios_Gangs"]:SubtractPlayerGangInfamy(source, "Valentine", 25):next(function(success)
    if success then
        print("Infamy subtracted.")
    end
end)
```

---

### `IsPlayerInGang`

Checks if a player is in a gang.

```lua
exports["EM_Studios_Gangs"]:IsPlayerInGang(source):next(function(isInGang)
    print("In gang?", isInGang)
end)
```

---

### `DoesGangControlZone`

Checks if a gang controls a zone (>= 500 infamy and no tie).

```lua
exports["EM_Studios_Gangs"]:DoesGangControlZone("The Outlaws", "Valentine"):next(function(result)
    if result then
        print("Gang controls this zone.")
    end
end)
```

---

### `GetPlayerGangZoneControlLevel`

Returns `"none"`, `"partial"`, or `"full"` control level of the player’s gang in a zone.

```lua
exports["EM_Studios_Gangs"]:GetPlayerGangZoneControlLevel(source, "Rhodes"):next(function(level)
    print("Control Level:", level)
end)
```

---

### `WithdrawZoneBalance`

Withdraws and clears the zone's gang balance (only if owner + controls zone).

```lua
exports["EM_Studios_Gangs"]:WithdrawZoneBalance(source, "Tumbleweed"):next(function(success)
    if success then
        print("Zone balance claimed.")
    end
end)
```

---

### `PayTaxToControllingGang`

Pays tax to the gang that controls the zone (if any).

```lua
exports["EM_Studios_Gangs"]:PayTaxToControllingGang("Strawberry", 15.0, source):next(function(success)
    if success then
        print("Tax paid to controlling gang.")
    end
end)
```

---

### `GetGangByCharId`

Fetches the gang name of a player from their character ID.

```lua
exports["EM_Studios_Gangs"]:GetGangByCharId(charId, function(gang)
    print("Player belongs to gang:", gang)
end)
```
