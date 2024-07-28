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
- [ ] [VORP](https://github.com/VORPCORE/vorp_core-lua)

## Installation
- [ ] Download and unzip the script
- [ ] Ensure the script in your server.cfg
- [ ] Configure the script
- [ ] Restart server


## Configuration


The configuration examples below, there are multiple config files there are alot of options to set up if you choose.


### ANIMALS CONFIG
```lua{% raw %}
Config = {}


------------------------------------------------------------ 𝔼ℝ𝔼𝔹𝕌𝕊 𝕎𝕀𝕃𝔻𝔼ℝℕ𝔼𝕊𝕊---------------------------------------------------------------------





------------------------------------------------------------------- 𝔹𝕪 𝔼𝕣𝕖𝕓𝕦𝕤-------------------------------------------------------------------------
-- This Config file is only for the animals, animal spawns are not controlled within this script only looting and skinning functions. Pelts are handled 
-- in the Pelt config script. This script you can set webhook and rewards along with mercykill ability and carcass deletion. if you have any questions
-- join the discord for support. https://discord.gg/pugmjxBKR8



Config.debug = false        -- FOR DEBUG ONLY
Config.mercyKill = true     -- ENABLE OR DISABLE MERCYKILL
Config.deleteCarcass = true -- ENABLE OR DISABLE CARCASS DELETING
Config.webhook = ''         -- DISCORD WEBHOOK
Config.webhookColor = 4286945
Config.webhookLogo = ''
Config.webhookFooterLogo = ''
Config.webhookAvatar = ''


----------------------------------------------------------------------  𝔸𝕟𝕚𝕞𝕒𝕝𝕤  -----------------------------------------------------------------------


Config.Animals = {
    [GetHashKey('a_c_armadillo_01')] = {                                            -- NAME OF THE ANIMAL MODEL
        name = "Armadillo",                                                         -- NAME OF THE ANIMAL FOR NOTIFICATION
        rewardItems = { "stringy", "armadilloc", "armadillos" },                    -- REWARD ITEMS FROM DATABASE
        rewardAmounts = { {1,3}, 1, 1 },                                            -- NUMBER OF REWARDS PER ITEM INSTEAD OF SINGLE NUMBER YOU CAN USE {1, 3} INSTEAD OF A SINGLE NUMBER AS SHOWN HERE
        displayNames = { "Stringy meat", "Armadillo claws", "Armadillo pelt" },     -- ITEM NAMES FOR NOTIFICATION
        type = "satchel_textures",                                                  -- TEXTURE DICTIONARY
        texture = "animal_armadillo",                                               -- TEXTURE
        color = "COLOR_WHITE",                                                      -- TEXTURE COLOR
    },
    [GetHashKey('A_C_Badger_01')] = {
        name = "American Badger",
        rewardItems = { "stringy", "scentg", "badgers" },
        rewardAmounts = { 1, 1, 1 },
        displayNames = { "Stringy meat", "Scent glad", "Badger skin" },
        texture = "animal_badger",
        color = "COLOR_WHITE",
    },
    [GetHashKey('A_C_Pronghorn_01')]  = {
        name = "American Pronghorn Doe",
        rewardItems = { "venison", "prongs" },
        rewardAmounts = { 1, 1 },
        displayNames = { "Vension", "Pronghorn pelt" },
        texture = "animal_pronghorn",
        color = "COLOR_WHITE",
    },
}


{% endraw %}```


THERE ARE MANY MORE CONFIG IN THE ACTUAL FILE THIS IS JUST FOR REFERENCE


### PLANTS CONFIG

```lua{% raw %}
Config = {}



------------------------------------------------------------ 𝔼ℝ𝔼𝔹𝕌𝕊 𝕎𝕀𝕃𝔻𝔼ℝℕ𝔼𝕊𝕊---------------------------------------------------------------------





---------------------------------------------------------------- 𝔹𝕪 𝔼𝕣𝕖𝕓𝕦𝕤---------------------------------------------------------------------------
--- Native plants are plants already permanantly in the world. It a model exists in the world it will allow gathering. The models and rewards and also
--- the textures can be changed but the locations are set and can not be moved.

--- Custom/added plants are set by the server owner/admin. The locations can be set along with all other variables. The models are optional and you can
--- spawn them with or without models. See examples if you need help join discord. https://discord.gg/pugmjxBKR8

-------------------------------------------------------------------ℕ𝕒𝕥𝕚𝕧𝕖 ℙ𝕝𝕒𝕟𝕥𝕤-----------------------------------------------------------------------

Config.PickDistance = 3.0 --DISTANCE YOU CAN GATHER THE PLANTS FROM
Config.Cooldown = 2 -- DEFAULT COOLDOWN IN MINUTES IF YOU FAILED TO SET IT BELOW
Config.key = 0x760A9C6F -- KEY TO GATHER PLANTS "G"

-- NATIVE PLANT MODELS IN THE WORLD AND THE GATHER REWARDS READ COMMENTS TO ADD MORE
Config.NativePlants = {
    [GetHashKey('crp_sugarcane_ab_sim')] = { -- MODEL OF THE PLANT IN THE WORLD 
        name = "Sugarcane",                  -- NAME OF THE PLANT
        rewardItems = { "sugarcane" },       -- NAME OF REWARD ITEM MUST BE IN DATABASE
        rewardAmounts = { 1 },               -- THE AMOUNT OF ITEMS REWARDED
        displayNames = { "Sugarcane" },      -- DISPLAY NAME
        type = "inventory_items",            -- TEXTURE DICTIONARY
        texture = "consumable_herb_saltbush",-- TEXTURE
        color = "COLOR_ORANGE",              --TEXTURE COLORS 
    },
    [GetHashKey('p_tree_orange_01')] = {
        name = "Orange",
        rewardItems = { "orange" },
        rewardAmounts = { 1 },
        displayNames = { "Orange" },
        type = "inventory_items",
        texture = "consumable_peach",
        color = "COLOR_ORANGE",
    },
    [GetHashKey('crp_berry_aa_sim')] = {
        name = "Raspberry",
        rewardItems = { "raspberry" },
        rewardAmounts = { 1 },
        displayNames = { "Raspberry" },
        type = "inventory_items",
        texture = "consumable_herb_red_raspberry",
        color = "COLOR_WHITE",
    },
}

-------------------------------------------------------------------ℂ𝕦𝕤𝕥𝕠𝕞 ℙ𝕝𝕒𝕟𝕥𝕤-------------------------------------------------------------------

Config.PlantAdd = {
    -- BELOW IS AN EXAMPLE OF A PLANT WITH PROP YOU CAN GET THE PROPS ON https://redlookup.com/ 
    -- AKA SPAWN WITH MODEL
    {
        name = "Tobacco Plant",                         -- PLANT NAME
        reward = "Indian_Tobbaco",                      -- REWARD ITEM (MUST BE IN DATABASE)
        plantModel = "s_indiantobacco01x",              -- PLANT MODEL TO SPAWN ( DONT USE THIS IF YOU DONT WANT TO SPAWN A MODEL )
        coords = vector3(2957.05, 2187.73, 170.2),   -- COORDINATES FOR PLANT TO SPAWN
        cooldown = 1,                                   -- COOLDOWN FOR THIS PLANT
        minReward = 1,                                  -- MINIMUM REWARD
        maxReward = 5,                                  -- MAXIMUM REWARD
        type = "inventory_items",                       -- TEXTURE DICTIONARY/TYPE
        texture = "consumable_herb_rams_head",          -- TEXTURE NAME
        color = "COLOR_WHITE",                          -- TEXTURE COLOR 
    },

    -- BELOW IS AN EXAMPLE OF A PLANT WITHOUT PROP FOR USE HOW YOU WANT DO NOT INCLUDE MODEL AND IT WILL NOT SPAWN A MODEL.
    -- AKA SPAWN WITHOUT MODEL
    {
        name = "Corn",
        reward = "corn",
        coords = vector3(2978.45, 2189.91, 166.5),
        cooldown = 1,
        minReward = 1,
        maxReward = 5,
        type = "inventory_items",
        texture = "consumable_corn",
        color = "COLOR_WHITE",
    },

}





{% endraw %}```


THERE ARE MANY MORE CONFIG IN THE ACTUAL FILE THIS IS JUST FOR REFERENCE











### PELTS CONFIG

```lua{% raw %}
Config.DeletePelts = true

Config.PeltHashes = {
    957520252,  -- Poor Bear Pelt
    143941906,  -- Good Bear Pelt
    1292673537, -- Perfect Bear Pelt

    -----ONLY USE HASHES FOR THE PELTS IF THERE ARE ANY MISSING AND YOU CAN NOT GET THEM LET US KNOW SO WE CAN UPDATE THE FILES
    


  }

{% endraw %}```


THERE ARE MANY MORE CONFIG IN THE ACTUAL FILE THIS IS JUST FOR REFERENCE

