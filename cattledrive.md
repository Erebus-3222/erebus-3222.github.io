---
layout: default
title: Cattle Drive
parent: Scripts
nav_order: 4
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
- [ ] [VORP](https://github.com/VORPCORE/vorp_core-lua)
- [ ] [BCC-UTILS](https://github.com/BryceCanyonCounty/bcc-utils)

## Installation
- [ ] Download and unzip the script
- [ ] Ensure the script in your server.cfg
- [ ] Configure the script
- [ ] Restart server


## Configuration


The configuration is defaulted below, feel free to add as many spawns as you want however keep in mind that the game has a hard limit of peds allowed.

```lua{% raw %}
Config = {
    debug = false, -- PROVIDES MANY CLIENT SIDE PRINTS TO HELP DEBUG ANY ISSUES.
    defaultlang = 'en_lang',
    Key = 0x760A9C6F, -- 'G' KEY -- SOME KEYS WORK OTHERS DON'T. CHANGE THIS AT YOUR OWN RISK.

    ------------------ HERD BEHAVIOR

    ---- BY DEFAULT, THE MORE CATTLE A PLAYER HAS, THE HARDER IT IS AND LONGER IT TAKES TO GET THEM TO THE SELLER ZONE. 
    ---- INCREASING WANDERCHANCE AND DECREASING MAXFOLLOWDISTANCE WILL MAKE IT EVEN HARDER, SO WILL DECREASING THE HERDTIMECHECK.

    MaxFollowDistance = 50.0, -- MAXIMUM DISTANCE BEFORE THE CATTLE STOP FOLLOWING.
    WanderChance = 5, -- THE CHANCE THAT THE COWS WILL RANDOMLY STOP FOLLOWING AND NEED TO BE CAPTURED AGAIN.
    WaitDistance = 7.0, -- THE DISTANCE THAT THE COWS WILL "WAIT" FOR THE PLAYER TO MOVE.
    PlayerMovementThreshold = 2.0, -- THE DISTANCE PLAYER MOVES BEFORE COWS START FOLLOWING AGAIN AFTER GETTING CLOSE.
    HerdTimeCheck = 20000, -- THE TIME BETWEEN DISTANCE AND WANDER CHECKS. 1000 = 1 SECOND 

    -------------- BUYER PED
    SpawnBuyerPed = true, -- ENABLE OR DISABLE NPC
    buyerPed = "u_f_m_tumgeneralstoreowner_01", -- NPC FOR THE SELL ZONE
    buyerBlip = 423351566, -- BLIP FOR THE SELL ZONE
    HerdBuyer = vector4(2618.3125, -791.3922, 42.4103, 182.7648), -- NPC COORDINATES 
    SellZoneCircle = vector3(2618.3125, -791.3922, 42.4103), -- THE CIRCLE THAT WILL SELL THE HERDED CATTLE
    SellZoneRadius = 7.5, -- RADIUS AROUND NPC WHERE SELLING OCCURS (IN METERS)
    SellZoneCircleGlow = true, -- ENABLE OR DISABLE THE GLOWING CIRCLE AROUND THE SELL ZONE
    GlowRed = 50, -- RANGE 0 - 255
    GlowGreen = 50, -- RANGE 0 - 255
    GlowBlue = 150, -- RANGE 0 - 255
    GlowTransparency = 255, -- RANGE 0 - 255

    ---------- REWARDS

    CurrencyType = 0, -- CURRENCY TYPE FOR PAYMENT (E.G., "MONEY", "GOLD", ETC.)
    HerdSalePrice = 50, -- EXAMPLE VALUE, PRICE PER COW SOLD
    rewardItems = false,
    itemRewards = {
       "meat",
       "feather",
    },
    
    --------------- HERD ZONES

    HerdZones = {
        {
            coords = vector3(431.8411, -19.5580, 109.3192), -- COORDS FOR THE CENTER OF THE ZONE
            radius = 25.0, -- RADIUS OF THE ZONE
            name = "Herd1", -- NAME OF THE HERD FROM HERDSPAWN SECTION BELOW. THE HERD NAME MUST MATCH 
            appearanceChance = 50, -- % CHANCE FOR THE HERD TO SPAWN WHEN PLAYER ENTERS THE AREA
        },

        -- {
        --     coords = vector3(2502.92, -1450.13, 46.31),
        --     radius = 15.0,
        --     name = "Zone2",
        --     appearanceChance = 50, -- 50% CHANCE
        -- }

        -- ADD MORE ZONES AS NEEDED
    },

    HerdSpawn = { -- THIS IS WHERE YOU DEFINE EACH SPAWN FOR DIFFERENT ZONES.
        Herd1 = { -- MUST MATCH NAME IN HERDZONES
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

        -- ADD MORE SPAWNS AS NEEDED
    }
}

{% endraw %}```

