---
layout: default
title: Erebus Item Admin
nav_order: 5
---

# Erebus Item Admin
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

If you need help please follow the instructions below.

## Requirements
- [ ] VORP (MORE FRAMEWORKS COMING)

## Installation
- [ ] Download and unzip the script
- [ ] Ensure the script in your server.cfg
- [ ] Configure the script
- [ ] Set your filepath in the config.lua
- [ ] Restart server OR Start script

## 📖 Commands Overview
- /additem2db: Opens the UI to add a new item.
- /searchitems: Opens the UI to search for items in the database.
- /searchweapons: Opens the UI to search for weapons by spawn name.


## How to use


This documentation covers the process of adding new items, searching for items and weapons, and uploading images for your in-game items. Follow the guide carefully to utilize all available features.

## 🛠️ Creating a New Item
To add a new item to the database, follow these steps:

Open the Item Creation UI:

Use the command /additem2db in-game.
This will open a form where you can input the item's information.
Fill in the Item Details:

Item Spawn Name: Enter the spawn name of the item. This is the internal name used for spawning and referencing the item in the game.
Label: Provide a display name for the item (this is what players will see).
Limit (Stack Size): Define the maximum number of this item that can be stacked.
Can Remove: Select whether the item can be removed from inventory (1 for Yes, 0 for No).
Type: If not specified, defaults to item_standard.
Usable: Select whether the item is usable (1 for Yes, 0 for No).
Description: Provide a brief description for the item (this will be displayed in the item tooltip in-game).
Submit the Item:

Click the Add Item button to submit the item to the database.
Upon successful submission, the item will be added, and you can start using it in the game.


## 🔍 Searching for Items and Weapons
There are two types of searches available:

1. Item Search:
Use the /searchitems command to open the Item Search UI.
A search bar will appear where you can type in the name or part of the name of the item.
The results will display the spawn name, display name, and a field indicating whether an image exists for that item (Yes/No).
2. Weapon Search:
Use the /searchweapons command to open the Weapon Search UI.
Like the item search, type the name or part of the name of the weapon to search.
The results will show the spawn name, display name, and the image status (Yes/No).
Image Availability Indicator:
The item and weapon search results will show if there is an associated image for the spawn name in the specified image directory.
Yes: An image with the same name exists.
No: No image exists for that spawn name.

##  ⚠️ Permissions and Restrictions
Only authorized users, as defined in the server configuration (Config.Developers), can use the /additem2db and /uploadimage commands. Ensure you have the correct permissions to avoid access errors.

## 🚨 Troubleshooting:
Image not showing in search? Ensure that the image is named exactly like the item's spawn name and is in the correct directory.
Command not working? Make sure you have the correct permissions and that the resource name hasn’t been altered.
By following this guide, you will be able to efficiently add and manage items and their associated images in your game.



