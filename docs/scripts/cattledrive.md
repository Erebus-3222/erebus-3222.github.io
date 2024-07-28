---
layout: default
title: Cattle Drive
parent: Scripts
---

# Cattle Drive
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

If you need help please follow the instructions below.

## Requirements
[VORP](https://github.com/VORPCORE/vorp_core-lua)
[BCC-UTILS](https://github.com/BryceCanyonCounty/bcc-utils)

## Installation
- [ ] Download and unzip the script
- [ ] Ensure the script in your server.cfg
- [ ] Configure the script
- [ ] Restart server


## Configuration


The configuration is defaulted below, feel free to add as many spawns as you want however keep in mind that the game has a hard limit of peds allowed.

```lua{% raw %}
Config = {
    debug = false, -- Provides many client side prints to help debug any issues.
    defaultlang = 'en_lang',
    Key = 0x760A9C6F, -- 'G' Key -- Some keys work others dont change this at your own risk.



------------------HERD BEHAVIOR

    ---- By default the more cattle a player has the harder it is and longer it takes to get them to the seller zone. 
    ---- Increasing WanderChance and decreasing MaxFollowDistance will make it even harder, so will decreasing the HerdTimeCheck.


    MaxFollowDistance = 50.0, -- Maximum distance before the cattle stop following.
    WanderChance = 5, -- The chance that the cows will randomly stop following and need to be captured again.
    WaitDistance = 7.0, -- The distance that the cows will "wait" for the player to move.
    PlayerMovementThreshold = 2.0, -- the distance player moves before cows start following again after getting close.
    HerdTimeCheck = 20000, -- the time between distance and wander checks. 1000 = 1 second 

-------------- BUYER PED
    SpawnBuyerPed = true, -- Enable or Disable NPC
    buyerPed = "u_f_m_tumgeneralstoreowner_01", -- NPC for the sell zone
    buyerBlip = 423351566, -- Blip for the sell zone
    HerdBuyer = vector4(2618.3125, -791.3922, 42.4103, 182.7648), -- NPC coordinates 
    SellZoneCircle = vector3(2618.3125, -791.3922, 42.4103), -- The Circle that will sell the herded cattle
    SellZoneRadius = 7.5, -- Radius around NPC where selling occurs (in meters)
    SellZoneCircleGlow = true, -- Enable or Disable The glowing circle around the sell zone
    GlowRed = 50,           -- Range 0 - 255
    GlowGreen = 50,         -- Range 0 - 255
    GlowBlue = 150,         -- Range 0 - 255
    GlowTransparency = 255, -- Range 0 - 255


---------- REWARDS

    CurrencyType = 0,  -- Currency type for payment (e.g., "money", "gold", etc.)
    HerdSalePrice = 50,  -- Example value, price per cow sold
    rewardItems = false,
    itemRewards = {
       "meat",
       "feather",
    },
    

---------------HERD ZONES


    HerdZones = {
        {
            coords = vector3(431.8411, -19.5580, 109.3192), ---coords for the center of the zone
            radius = 25.0, -- radius of the zone
            name = "Herd1", --Name of the herd from HerdSpawn section below, the herd name must match 
            appearanceChance = 50, -- % chance for the herd to spawn when player enters the area
        },

        -- {
        --     coords = vector3(2502.92, -1450.13, 46.31),
        --     radius = 15.0,
        --     name = "Zone2",
        --     appearanceChance = 50, -- 50% chance
        -- }

        -- Add more zones as needed
    },
    HerdSpawn = {-- this is where you define each spawn for different zones. 
        Herd1 = {--MUST MATCH NAME IN HERDZONES
            { model = 'A_C_Cow', spawnpoint = vector4(424.6364, -47.6337, 109.1254, 116.2319) },
            { model = 'A_C_Cow', spawnpoint = vector4(413.1532, -57.4077, 110.3754, 67.4843) },
            { model = 'A_C_Cow', spawnpoint = vector4(393.8228, -56.5883, 110.1550, 54.7916) },
            { model = 'A_C_Cow', spawnpoint = vector4(389.2286, -41.9948, 109.9951, 356.2169) },
            { model = 'A_C_Cow', spawnpoint = vector4(388.9354, -16.6511, 108.4244, 333.5460) },
            { model = 'A_C_Cow', spawnpoint = vector4(397.9000, 5.2379, 107.7955, 6.5744) },
            { model = 'a_c_bull_01', spawnpoint = vector4(423.8056, 16.5907, 108.6001, 262.3212) },
        },
      
        -- Zone2 = {
        --     { model = 'A_C_Cow', spawnpoint = vector4(1293.0657, -6869.9204, 43.2063, 226.7794) },
        --     { model = 'A_C_Cow', spawnpoint = vector4(1290.8406, -6860.7803, 43.1331, 180.6018) }
        -- }

        -- Add more spawns as needed
    }
}
{% endraw %}```

