
Certainly! Below is a comprehensive step-by-step tutorial on configuring **CrazyCrates** for your Minecraft server using the provided configuration file. This guide will walk you through understanding each section of the configuration, customizing your crate, setting up rewards, and ensuring everything works seamlessly.

---

## **Tutorial: Configuring CrazyCrates with a Custom Crate Configuration**

### **Table of Contents**

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Installation of CrazyCrates](#installation-of-crazycrates)
4. [Accessing and Understanding the Configuration File](#accessing-and-understanding-the-configuration-file)
5. [Step-by-Step Configuration](#step-by-step-configuration)
   - [1. Basic Crate Settings](#1-basic-crate-settings)
   - [2. GUI Customization](#2-gui-customization)
   - [3. Broadcast and Commands](#3-broadcast-and-commands)
   - [4. Sound Settings](#4-sound-settings)
   - [5. Prize Configuration](#5-prize-configuration)
   - [6. Hologram Settings](#6-hologram-settings)
6. [Saving and Applying the Configuration](#saving-and-applying-the-configuration)
7. [Testing Your Crate](#testing-your-crate)
8. [Advanced Customizations](#advanced-customizations)
9. [Conclusion](#conclusion)

---

### **Introduction**

**CrazyCrates** is a versatile Minecraft plugin that allows server administrators to create customizable crates. These crates can enhance player engagement by offering exciting rewards, and they also provide monetization opportunities for server owners. This tutorial will guide you through configuring a custom crate using the provided YAML configuration file.

---

### **Prerequisites**

Before you begin, ensure you have the following:

- **Minecraft Server:** Running the version compatible with CrazyCrates.
- **CrazyCrates Plugin:** Downloaded from a trusted source (e.g., [SpigotMC](https://www.spigotmc.org/resources/crazycrates.17597/)).
- **Permissions Plugin (Optional):** Such as LuckPerms if you plan to use permission-based features.
- **PlaceholderAPI (Optional):** For advanced placeholders in messages.
- **Basic Knowledge of YAML:** Understanding indentation and syntax.

---

### **Installation of CrazyCrates**

1. **Download CrazyCrates:**
   - Visit the [official CrazyCrates page](https://www.spigotmc.org/resources/crazycrates.17597/) and download the latest version compatible with your server.

2. **Install the Plugin:**
   - Place the `CrazyCrates.jar` file into your server's `plugins` directory.

3. **Restart Your Server:**
   - Restart the server to generate the necessary configuration files.

4. **Verify Installation:**
   - Ensure that CrazyCrates is loaded correctly by typing `/crates` in the server console or in-game.

---

### **Accessing and Understanding the Configuration File**

After installation, navigate to the `plugins/CrazyCrates` directory. Here, you'll find configuration files, including `config.yml` and individual crate configuration files.

For this tutorial, we'll focus on a custom crate configuration file. You can create a new YAML file (e.g., `AdvancedCrate.yml`) or modify an existing one.

---

### **Step-by-Step Configuration**

Let's break down the provided configuration file and understand each section to customize your crate effectively.

#### **1. Basic Crate Settings**

```yaml
CrateType: CSGO
StartingKeys: 0
RequiredKeys: 10
Max-Mass-Open: 10
InGUI: true
Slot: 13
```

- **CrateType:** Determines the animation and behavior of the crate. `CSGO` is a predefined type, but you can explore others or create custom types.
  
- **StartingKeys:** The number of keys a player receives when they first join the server. Set to `0` to start without keys.
  
- **RequiredKeys:** The number of keys needed to open the crate. Players need to have at least `10` keys to open this crate.
  
- **Max-Mass-Open:** The maximum number of crates a player can open at once using `/crates mass-open`. Set to `10`.
  
- **InGUI:** If `true`, the crate appears in the CrazyCrates GUI.
  
- **Slot:** The inventory slot where the crate will appear in the GUI. Slot `13` corresponds to the center slot in a standard chest GUI.

#### **2. GUI Customization**

```yaml
Item: "chest"
Custom-Model-Data: -1
Glowing: false
Name: "<bold><light_purple>Advanced Crate</bold>"
Lore:
  - "<gray>This crate contains strange objects."
  - "<gray>You have <gold>%keys% keys <gray>to open this crate with."
  - "<gray>You have opened this crate: <gold>%crate_opened% times"
  - "<gray>(<yellow>!<gray>) Right click to view rewards."
```

- **Item:** The item representing the crate in the GUI. Here, it's a `chest`.
  
- **Custom-Model-Data:** Custom model data for the item. `-1` disables it.
  
- **Glowing:** If `true`, the item will have an enchanted glow effect.
  
- **Name:** The display name of the crate in the GUI. Supports color and formatting codes.
  
- **Lore:** Additional information displayed below the item name. Placeholders like `%keys%` and `%crate_opened%` dynamically show player-specific data.

#### **3. Broadcast and Commands**

```yaml
OpeningBroadCast: true
BroadCast: "%prefix%<bold><gold>%player%</bold><reset> <gray>is opening a <bold><light_purple>Advanced Crate.</bold>"
opening-command:
  toggle: false
  commands:
    - "put your command here."
Settings:
  Broadcast:
    Toggle: false
    Messages:
      - "<red>%player% won the prize <yellow>%reward%."
    Permission: ""
```

- **OpeningBroadCast:** If `true`, broadcasts a message when a player opens the crate.
  
- **BroadCast:** The message to broadcast. Uses placeholders like `%player%` for the player's name.
  
- **opening-command:**
  - **toggle:** If `true`, executes commands when the crate is opened.
  - **commands:** List of commands to execute. Placeholders like `%player%` are supported.
  
- **Settings > Broadcast:**
  - **Toggle:** Enables or disables broadcast messages when a player wins a prize.
  - **Messages:** List of messages to broadcast upon winning.
  - **Permission:** Players with this permission won't trigger the broadcast.

#### **4. Sound Settings**

```yaml
sound:
  cycle-sound:
    toggle: true
    value: "block.note_block.xylophone"
    volume: 1.0
    pitch: 1.0
  click-sound:
    toggle: true
    value: "ui.button.click"
    volume: 1.0
    pitch: 1.0
  stop-sound:
    toggle: true
    value: "entity.player.levelup"
    volume: 1.0
    pitch: 1.0
```

- **cycle-sound:** Sound played during the crate animation.
  
- **click-sound:** Sound played when a player clicks the crate.
  
- **stop-sound:** Sound played when the crate opening process finishes.
  
- **Parameters:**
  - **toggle:** Enables or disables the specific sound.
  - **value:** The sound effect to play. Refer to [Minecraft Sound List](https://minecraft.fandom.com/wiki/Sounds.json#Java_Edition_values) for available sounds.
  - **volume & pitch:** Control the sound's loudness and pitch.

#### **5. Prize Configuration**

##### **Default Prize Messages and Commands**

```yaml
Prize-Message:
  - "<gray>You have won <red>%reward% <gray>from <red>%crate%."
Prize-Commands: []
```

- **Prize-Message:** Default message displayed when a player wins a prize without a specific message.
  
- **Prize-Commands:** Default commands executed when a prize is won. Empty by default.

##### **Defining Prizes**

```yaml
Prizes:
  "1":
    DisplayName: "<bold><dark_red>Warlord's Set</bold>"
    DisplayItem: "netherite_helmet"
    Settings:
      Custom-Model-Data: -1
    DisplayEnchantments:
      - "protection:5"
      - "unbreaking:3"
    DisplayTrim:
      Material: "redstone"
      Pattern: "sentry"
    DisplayAmount: 1
    DisplayLore:
      - "<gray>Win the warlord's set."
      - "<bold><gold>Chance: <red>40%</bold>"
    Weight: 40.0
    Commands:
      - "lp user %player% permission set crazycrates.blacklist.warlord"
    Items:
      - "Item:netherite_helmet, Amount:1, Damage:25, Trim-Pattern:sentry, Trim-Material:redstone, Name:<bold><dark_red>Warlord's Helmet</bold>, protection:5, unbreaking:3"
      - "Item:netherite_chestplate, Amount:1, Damage:25, Trim-Pattern:sentry, Trim-Material:redstone, Name:<bold><dark_red>Warlord's Chestplate</bold>, protection:5, unbreaking:3"
      - "Item:netherite_leggings, Amount:1, Damage:25, Trim-Pattern:sentry, Trim-Material:redstone, Name:<bold><dark_red>Warlord's Leggings</bold>, protection:5, unbreaking:3"
      - "Item:netherite_boots, Amount:1, Damage:25, Trim-Pattern:sentry, Trim-Material:redstone, Name:<bold><dark_red>Warlord's Boots</bold>, protection:5, unbreaking:3"
    BlackListed-Permissions:
      - "crazycrates.blacklist.warlord"
    Alternative-Prize:
      Toggle: true
      Messages:
        - "<reset> <dark_gray>[<blue>CrazyCrates<dark_gray>]: <gray>You have already won that prize, so enjoy some gold nuggets."
      Commands:
        - "give %player% gold_nugget 16"
      Items:
        - "Item:gold_nugget, Amount:16"
```

- **Prizes:** A list of all possible prizes in the crate, identified by unique keys (`"1"`, `"2"`, etc.).
  
- **Each Prize Includes:**
  
  - **DisplayName:** Name shown in the GUI.
    
  - **DisplayItem:** The item displayed as the prize.
    
  - **Settings:**
    - **Custom-Model-Data:** Custom model data for the item.
  
  - **DisplayEnchantments:** Enchantments applied to the display item.
  
  - **DisplayTrim:**
    - **Material & Pattern:** Adds decorative trims to armor items.
  
  - **DisplayAmount:** Quantity shown in the GUI.
  
  - **DisplayLore:** Descriptive text and chance percentage.
  
  - **Weight:** Determines the probability of winning this prize. Lower numbers mean higher chances.
  
  - **Commands:** Commands executed when the prize is won. Here, it adds a blacklist permission to prevent re-winning.
  
  - **Items:** Detailed list of items awarded. Includes item type, amount, damage (durability), trim details, name, and enchantments.
  
  - **BlackListed-Permissions:** Permissions that, if held by a player, prevent them from winning this prize again.
  
  - **Alternative-Prize:**
    - **Toggle:** Enables an alternative prize if the main prize is blacklisted.
    - **Messages:** Informational message to the player.
    - **Commands:** Commands to execute for the alternative prize.
    - **Items:** Items to give as the alternative prize.

##### **Second Prize Example**

```yaml
"2":
  DisplayEnchantments:
    - "protection:5"
    - "unbreaking:3"
  DisplayItem: "enchanted_book"
  Settings:
    Custom-Model-Data: -1
  DisplayAmount: 3
  DisplayLore:
    - "<gradient:#8fcfa0:#32a852>A gradient lore!"
  Weight: 25.0
  Items:
    - "Item:enchanted_book, protection:5, unbreaking:3"
```

- **Simpler Prize Configuration:** This prize is an enchanted book with specific enchantments.
  
- **DisplayLore:** Uses a gradient color for the lore text.
  
- **Weight:** `25.0` implies a 40% chance for the first prize (`40.0`) vs. `25.0` here.

#### **6. Hologram Settings**

```yaml
Hologram:
  Toggle: true
  Height: 1.5
  Range: 8
  Update-Interval: -1
  Color: "transparent"
  Message:
    - "<bold><light_purple>Advanced Crate</bold>"
```

- **Toggle:** Enables or disables holograms for the crate.
  
- **Height:** Height above the crate where the hologram appears.
  
- **Range:** Distance from which players can see the hologram.
  
- **Update-Interval:** How often the hologram updates. `-1` disables automatic updates.
  
- **Color:** Background color using hex codes. `transparent` means no color.
  
- **Message:** The text displayed in the hologram. Supports formatting codes.

---

### **Saving and Applying the Configuration**

1. **Save the Configuration File:**
   - After editing the YAML file, save your changes ensuring proper indentation (YAML is sensitive to spaces).

2. **Reload or Restart the Server:**
   - For changes to take effect, you can either:
     - **Reload CrazyCrates:** `/crate reload` or `/cc reload`
     - **Restart the Server:** Ensures all configurations are loaded fresh.

3. **Check for Errors:**
   - Monitor the server console for any errors related to CrazyCrates. Correct any syntax issues if they arise.

---

### **Testing Your Crate**

1. **Obtain Keys:**
   - Since `StartingKeys` is set to `0`, you may need to manually give yourself keys for testing.
   - Use the command: `/crates givekeys <player> 10` to give 10 keys.

2. **Access the Crate GUI:**
   - Use the command: `/crates` to open the CrazyCrates GUI.
   - Locate your **Advanced Crate** in slot `13`.

3. **Open the Crate:**
   - Click on the crate to initiate the opening process.
   - Observe the sounds, broadcast messages, and animations to ensure they function as configured.

4. **Verify Prize Distribution:**
   - After opening, check if the correct items are awarded.
   - Test the blacklist feature by attempting to win the same prize again and verifying the alternative prize is given.

5. **Hologram Visibility:**
   - Ensure the hologram appears above the crate at the specified height and within the defined range.

---

### **Advanced Customizations**

- **Custom Crate Types:**
  - Explore different `CrateType` options or create your own animations by following the [CrazyCrates Crate Types Documentation](https://docs.crazycrew.us/docs/plugins/crazycrates/misc/crate-types).

- **Integrate with Economy Plugins:**
  - Link crate keys to in-game or real-money purchases using economy plugins for monetization.

- **Dynamic Messages:**
  - Utilize PlaceholderAPI for dynamic and interactive messages within broadcasts and prize notifications.

- **Event-Driven Crates:**
  - Configure crates to appear during specific server events or milestones to boost engagement.

- **Custom Model Data:**
  - Use custom model data to assign unique textures or models to crate items, enhancing visual appeal.

---

### **Conclusion**

Configuring **CrazyCrates** offers a robust way to enhance your Minecraft server's gameplay experience. By following this tutorial, you've set up a customized crate with dynamic rewards, engaging sounds, and interactive GUI elements. Remember to continually test and refine your configurations based on player feedback to maintain an exciting and rewarding environment.

For further customization and advanced features, refer to the [CrazyCrates Documentation](https://docs.crazycrew.us/docs/category/crazycrates) and participate in community forums for tips and support.

Happy Crating!
