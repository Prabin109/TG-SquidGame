# TG SquidGame - Complete Setup Tutorial (Version 1.2)

This tutorial will guide you through setting up and running your first Red Light Green Light game arena with all the latest improvements and features.

**Requirements:**
- Paper 1.21.1+ or Spigot 1.21.1+
- Java 21 or higher
- TG-SquidGame v1.2

---

## Table of Contents

1. [Installation](#installation)
2. [Creating Your First Arena](#creating-your-first-arena)
3. [Configuring Arena Positions](#configuring-arena-positions)
4. [Using the GUI Editor](#using-the-gui-editor)
5. [Starting a Game](#starting-a-game)
6. [Player Experience](#player-experience)
7. [Advanced Configuration](#advanced-configuration)
8. [Troubleshooting](#troubleshooting)

---

## Installation

### Step 1: Install the Plugin

**Prerequisites:**
- Ensure your server is running **Java 21 or higher**
- Use **Paper 1.21.1+** (recommended) or **Spigot 1.21.1+**

**Installation:**
1. Download `TG-SquidGame-1.2.jar`
2. Place it in your server's `plugins` folder
3. Start or restart your Minecraft server
4. Check the console for the message: `TG SquidGame v1.2 by Techinpoint Gamerz has been enabled!`

### Step 2: Verify Installation

Run the command:
```
/tgsg
```

You should see the help menu with all available commands.

---

## Creating Your First Arena

### Step 1: Create the Arena File

Choose a location in your world where you want to build the arena. Then run:

```
/tgsg create myarena RedLightGreenLight
```

Replace `myarena` with your preferred arena name (no spaces).

**Expected Output:**
```
Arena 'myarena' created successfully!
Configure it with: /tgsg myarena setpos1, setpos2, etc.
```

---

## Configuring Arena Positions

To set up an arena, you need to define 8 key locations. Here's the recommended order:

### Step 2: Define Arena Boundaries

Stand at one corner of where you want your arena to be:
```
/tgsg myarena setpos1
```

Walk to the opposite corner (diagonal):
```
/tgsg myarena setpos2
```

**Tip:** These two points define a 3D rectangular region. Everything inside is the arena.

### Step 3: Define Starting Area

Stand at one corner of where players should spawn:
```
/tgsg myarena setstart1
```

Walk to the opposite corner of the starting area:
```
/tgsg myarena setstart2
```

**Tip:** Players will be randomly spawned within this region when the game starts.

### Step 4: Define Win Zone

Stand at one corner of the finish line:
```
/tgsg myarena setwin1
```

Walk to the opposite corner:
```
/tgsg myarena setwin2
```

**Tip:** Players who reach this zone win the game.

### Step 5: Set Lobby Spawn

Stand where players should wait before the game starts:
```
/tgsg myarena setlobby
```

### Step 6: Set Spectator Spawn

Stand where eliminated/winning players should spectate from:
```
/tgsg myarena setspec
```

**Tip:** Choose a location with a good view of the arena.

### Step 7: Save Your Configuration

```
/tgsg myarena save
```

**Expected Output:**
```
Arena 'myarena' saved successfully!
```

### Step 8: Arena Setup Completion (New in v1.2)

When you set the final required position, you'll see a **yellow success message**:
```
Arena setup completed successfully! All positions are now set.
```

This confirms that your arena is fully configured and ready for use. You can verify this by running:
```
/tgsg list
```

Your arena should now show as "Ready" with a green status indicator.

---

## Using the GUI Editor

The GUI editor allows you to adjust arena settings without manually editing YAML files. **Version 1.2** features an enhanced interface with improved visual design.

### Opening the Editor

```
/tgsg myarena edit
```

A graphical interface will open with the following options:

### Time Limit Setting

- **Item:** Clock (⏰)
- **Action:** Click to cycle through time options (60s, 90s, 120s, 150s, 180s, etc.)
- **Purpose:** Sets how long the game runs before ending

### Minimum Players Setting (New in v1.2)

- **Item:** Player Head (👥)
- **Visual:** Enhanced lore with Unicode symbols and color coding
- **Actions:**
  - **Left Click:** +1 player (Green)
  - **Right Click:** -1 player (Red)
  - **Shift + Left Click:** +5 players (Green)
  - **Shift + Right Click:** -5 players (Red)
- **Purpose:** Sets minimum players required before game can start

### Auto-Start Timer (New in v1.2)

- **Item:** Clock (⏱)
- **Visual:** Professional lore with clear action descriptions
- **Actions:**
  - **Left Click:** +5 seconds (Green)
  - **Right Click:** -5 seconds (Red)
  - **Shift + Left Click:** +30 seconds (Green)
  - **Shift + Right Click:** -30 seconds (Red)
- **Purpose:** Sets countdown timer when minimum players are reached

### Barrier Toggle

- **Item:** Barrier block
- **Action:** Click to enable/disable barriers
- **Purpose:** When enabled, invisible barrier blocks surround the arena perimeter

### Sound Toggle

- **Item:** Note block
- **Action:** Click to enable/disable sounds
- **Purpose:** Controls whether players hear sound effects during the game

### Save Button

- **Item:** Emerald
- **Action:** Click to save all changes and exit
- **Purpose:** Commits your changes to the arena configuration file

### Canceling Changes

If you made changes you don't want to keep:
```
/tgsg myarena cancel
```

---

## Starting a Game

### Step 1: Verify Arena is Ready

```
/tgsg list
```

Your arena should show as "Ready" (green status). If it shows "Incomplete" (red), you need to set all positions.

### Step 2: Have Players Join

Players can join the arena with:
```
/tgsg myarena join
```

They will be teleported to the lobby spawn point.

### Step 3: Auto-Start Feature (New in v1.2)

The game can now start automatically when the minimum number of players join:

1. **Minimum Players Reached:** When enough players join, an auto-start countdown begins
2. **Countdown Display:** Players see the countdown in chat and BossBar
3. **Manual Override:** Admins can still manually start before the timer expires

### Step 4: Manual Start (Traditional Method)

When ready, an admin can manually start:
```
/tgsg myarena start
```

**What Happens:**
1. 5-second countdown begins (players stay in their current positions - **v1.2 improvement**)
2. BossBar appears showing countdown
3. After countdown, game starts with "GREEN LIGHT - GO!"
4. Barriers (if enabled) appear around the arena
5. Game timer begins

### Game Start Countdown (v1.2 Improvement)

**Important Change:** Players are **no longer teleported** during the 5-second countdown. This means:

- Players start the game from wherever they are standing when countdown ends
- No unwanted teleportation during countdown phase
- More strategic positioning opportunities
- Smoother game start experience

**Recommendation:** Have players position themselves in the starting area before the countdown begins.

---

## Player Experience

### During Green Light

- **BossBar:** Shows "🟢 GREEN LIGHT - GO!" in green
- **Sound:** High-pitched chime sound plays
- **Action:** Players can move freely toward the win zone

### During Red Light

- **BossBar:** Shows "🔴 RED LIGHT - STOP!" in red
- **Sound:** Low bass sound plays
- **Action:** Players must freeze completely
- **Penalty:** Moving even slightly results in instant elimination

### Elimination

When eliminated:
- Player receives message: "You moved during RED LIGHT! You are eliminated."
- Instantly enters spectator mode
- Teleported to spectator spawn point
- Lightning sound effect plays
- Can watch the rest of the game

### Winning

When a player reaches the win zone:
- Broadcast message: "⭐ [Player] has reached the finish line!"
- Player receives: "Congratulations! You won!"
- Victory sound plays
- Enters spectator mode to watch remaining players

### Game End

The game ends when:
- Time runs out, OR
- All players are eliminated or have won

All players are returned to the lobby spawn point.

---

## Advanced Configuration

### Manual YAML Editing

Arena files are located in `plugins/TG-SquidGame/arenas/`

Example `myarena.yml` (v1.2):
```yaml
arena:
  name: "myarena"
  type: "RedLightGreenLight"
  world: "world"
  pos1: "100,65,100"
  pos2: "150,75,150"
  startPos1: "110,65,110"
  startPos2: "120,65,120"
  winPos1: "145,65,145"
  winPos2: "150,65,150"
  lobby: "90,65,90"
  spectator: "160,70,160"
  barrierEnabled: true
  timeLimit: 180
  randomLogic: "complex"
  soundEnabled: true
  minPlayers: 2          # New in v1.2
  autoStartTimer: 30     # New in v1.2
```

### New Configuration Options (v1.2)

- `minPlayers`: Minimum players required before auto-start begins (default: 2)
- `autoStartTimer`: Seconds to wait before auto-starting when minimum players reached (default: 30)

### Custom GUI Configuration (Enhanced in v1.2)

You can customize the GUI by editing the `gui` section:

```yaml
gui:
  name: "&6Custom Arena Settings"
  size: 45  # Must be multiple of 9 (9, 18, 27, 36, 45, 54)
  items:
    timeLimit:
      slot: 11  # Inventory slot (0-44 for size 45)
      name: "&a⏰ Custom Time Name"
      lore:
        - "&7Your custom description"
        - "&7Second line"
    minPlayers:
      slot: 13
      name: "&b👥 Player Requirements"
      lore:
        - "&bMinimum Players: &f{minPlayers}"
        - "&7Click to adjust"
    autoStartTimer:
      slot: 15
      name: "&e⏱ Auto-Start Settings"
      lore:
        - "&eTimer: &f{autoStartTimer} seconds"
        - "&7Click to modify"
```

### Random Logic Options

- `complex`: Light phases last 4-10 seconds (unpredictable)
- `simple`: Light phases last 5-10 seconds (slightly more predictable)

Edit in the arena file:
```yaml
randomLogic: "complex"
```

### Global Settings (Updated for v1.2)

Edit `plugins/TG-SquidGame/config.yml`:

```yaml
settings:
  prefix: "&6[TG SquidGame]&r "
  defaultTimeLimit: 180
  countdownTimer: 5
  enableJoinMessage: true
  soundEffects: true
  defaultBossBarColor: "GREEN"
  useComplexRandomLogic: true
  
game:
  # Default game settings
  startCountdown: 5  # seconds before game starts
  defaultGameTime: 180  # seconds for game duration
  movementThreshold: 0.15  # distance threshold for movement detection
  
arena:
  # Arena-specific settings
  autoSaveOnEdit: false  # whether to auto-save when exiting edit mode
  requireEditModeForSave: true  # require edit mode to use save command
```

**New Options Explained:**
- `countdownTimer`: Duration of countdown before game starts
- `startCountdown`: Game-specific countdown setting
- `defaultGameTime`: Default duration for new arenas
- `movementThreshold`: Sensitivity for red light movement detection (0.15 = very sensitive)
- `autoSaveOnEdit`: Automatically save when exiting edit mode
- `requireEditModeForSave`: Must be in edit mode to save changes

After editing, reload:
```
/tgsg reload
```

---

## Troubleshooting

### Problem: "Arena is not fully configured"

**Solution:** Make sure you've set all 8 positions:
- pos1 and pos2 (arena boundaries)
- startPos1 and startPos2 (spawn area)
- winPos1 and winPos2 (finish line)
- lobby (waiting area)
- spectator (observer location)

Verify with:
```
/tgsg list
```

### Problem: Players can leave the arena during the game

**Solution:** Check that pos1 and pos2 properly enclose the entire play area.

### Problem: "World 'worldname' not found"

**Solution:** The arena file references a world that doesn't exist. Edit the arena file and change the `world:` value to match your world name (usually "world", "world_nether", or "world_the_end").

### Problem: Barriers don't appear

**Solution:**
1. Check if barriers are enabled: `/tgsg myarena edit`
2. Ensure pos1 and pos2 are set correctly
3. Try disabling and re-enabling:
   ```
   /tgsg myarena disablebarrier
   /tgsg myarena enablebarrier
   /tgsg myarena save
   ```

### Problem: Players aren't eliminated during red light

**Solution:** This is by design - only significant movement triggers elimination. The threshold is very small (0.15 blocks), but players must actually move, not just look around.

### Problem: Game won't start

**Solution:** Check these requirements:
1. Arena must be fully configured (all positions set)
2. At least the minimum number of players must have joined (check with GUI editor)
3. No game is currently running in that arena
4. **New in v1.2:** Check if auto-start timer is enabled and wait for countdown

### Problem: Auto-start isn't working (New in v1.2)

**Solution:**
1. Check minimum players setting: `/tgsg myarena edit`
2. Ensure enough players have joined: `/tgsg list`
3. Verify auto-start timer is set above 0 seconds
4. Check if manual start was used (overrides auto-start)

### Problem: Players complain about teleportation during countdown

**Solution:** This was fixed in v1.2! Players are no longer teleported during the 5-second countdown. If you're still experiencing this, ensure you're using TG-SquidGame v1.2 or later.

### Problem: Java version errors

**Solution:** TG-SquidGame v1.2 requires Java 21 or higher. Update your server's Java version:
1. Download Java 21 from Oracle or OpenJDK
2. Update your server startup script to use Java 21
3. Restart your server

### Problem: GUI items don't work

**Solution:**
1. Make sure you opened the GUI with `/tgsg myarena edit`
2. Verify you're in edit mode before clicking items
3. Try closing and reopening the GUI

---

## Building a Great Arena

### Design Tips

1. **Distance:** Make the start-to-finish distance 30-50 blocks for balanced gameplay
2. **Height:** Keep the arena relatively flat or use gentle slopes
3. **Visibility:** Ensure players can see the win zone from the starting area
4. **Spectator View:** Position the spectator spawn point above or to the side for a good view
5. **Lobby:** Place the lobby outside the arena boundaries
6. **Width:** Allow 10-20 blocks of width so players can spread out

### Example Coordinates

For a basic 40-block straightaway arena:

```
/tgsg myarena setpos1        → Stand at 100, 64, 100
/tgsg myarena setpos2        → Stand at 100, 74, 200
/tgsg myarena setstart1      → Stand at 100, 64, 100
/tgsg myarena setstart2      → Stand at 110, 64, 110
/tgsg myarena setwin1        → Stand at 100, 64, 190
/tgsg myarena setwin2        → Stand at 110, 64, 200
/tgsg myarena setlobby       → Stand at 105, 64, 90
/tgsg myarena setspec        → Stand at 105, 80, 150
```

---

## Quick Reference Card

### Essential Commands

| Task | Command |
|------|---------|
| Create arena | `/tgsg create <name> RedLightGreenLight` |
| Set boundaries | `/tgsg <name> setpos1` and `setpos2` |
| Set spawn area | `/tgsg <name> setstart1` and `setstart2` |
| Set win zone | `/tgsg <name> setwin1` and `setwin2` |
| Set lobby | `/tgsg <name> setlobby` |
| Set spectator | `/tgsg <name> setspec` |
| Save arena | `/tgsg <name> save` |
| Edit settings | `/tgsg <name> edit` |
| Join arena | `/tgsg <name> join` |
| Start game | `/tgsg <name> start` |
| Stop game | `/tgsg <name> stop` |
| List arenas | `/tgsg list` |
| Reload config | `/tgsg reload` |

---

## Next Steps

Now that you have your first arena set up:

1. Test the game with friends
2. Adjust time limits and settings based on feedback
3. Build additional arenas for variety
4. Experiment with different arena layouts and themes
5. Create obstacle courses or themed environments

Stay tuned for future updates with new minigames!

---

**Developed by Techinpoint Gamerz (TG)**
**Version 1.2**
**Requirements: Java 21+, Paper/Spigot 1.21.1+**

### What's New in Version 1.2?
- ✅ Fixed teleportation bug during countdown
- ✅ Enhanced GUI with improved visual design
- ✅ Arena setup completion notifications
- ✅ Auto-start feature with minimum players
- ✅ Migrated to Paper API with Java 21
- ✅ Professional polish and improvements

Enjoy your enhanced Squid Game experience!
