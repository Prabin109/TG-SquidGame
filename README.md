# TG SquidGame Plugin

**Version:** 1.1
**Author:** Techinpoint Gamerz (TG)
**Minecraft Version:** 1.21.1+
**Server Type:** Paper (recommended), Spigot compatible
**Java Requirement:** Java 21+

---

## Overview

TG SquidGame is a professional modular Minecraft minigame plugin inspired by the popular Squid Game series. This plugin supports multiple arenas in a single world and is designed for easy expansion. Currently features the **Red Light Green Light** minigame with enhanced gameplay mechanics and improved user experience.

### Key Features

- **Multi-Arena Support**: Run multiple game arenas simultaneously in one world
- **Modular Design**: Easy to extend with new minigames
- **Enhanced GUI Configuration**: Intuitive in-game editor with improved visual design
- **YAML-Based Setup**: Each arena has its own configuration file
- **Barrier System**: Automatic arena boundaries using barrier blocks
- **Spectator Mode**: Eliminated players can spectate the ongoing game
- **Disconnect Handling**: Players who disconnect are automatically eliminated
- **BossBar Integration**: Real-time game state display
- **Sound Effects**: Immersive audio cues for game events
- **Setup Completion Feedback**: Clear notifications when arena configuration is complete
- **Improved Countdown System**: No unwanted teleportation during game countdown
- **Minimum Players & Auto-Start**: Configurable player requirements and automatic game starting

---

## Installation

### Requirements
- **Server Software**: Paper 1.21.1+ (recommended) or Spigot 1.21.1+
- **Java Version**: Java 21 or higher
- **Minecraft Version**: 1.21.1+

### Installation Steps
1. Download the `TG-SquidGame-1.2.jar` file
2. Ensure your server is running Java 21 or higher
3. Place the JAR file in your server's `plugins` folder
4. Restart your server
5. The plugin will create necessary directories and files:
   - `plugins/TG-SquidGame/config.yml` - Main configuration
   - `plugins/TG-SquidGame/messages.yml` - Customizable messages
   - `plugins/TG-SquidGame/arenas/` - Arena configuration files

---

## Configuration

### Main Config (`config.yml`)

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

**Configuration Options:**

- `prefix`: Chat message prefix for all plugin messages
- `defaultTimeLimit`: Default game duration in seconds
- `countdownTimer`: Countdown duration before game starts
- `enableJoinMessage`: Show messages when players join arenas
- `soundEffects`: Enable/disable sound effects globally
- `defaultBossBarColor`: Default BossBar color (GREEN, RED, BLUE, etc.)
- `useComplexRandomLogic`: Use advanced randomization for light changes
- `startCountdown`: Seconds of countdown before game begins
- `defaultGameTime`: Default duration for games
- `movementThreshold`: Sensitivity for movement detection during red light
- `autoSaveOnEdit`: Automatically save arena when exiting edit mode
- `requireEditModeForSave`: Require edit mode to use save command

### Arena Configuration

Each arena has its own `.yml` file in the `arenas` folder. Example: `redlight1.yml`

```yaml
arena:
  name: "redlight1"
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
  minPlayers: 2
  autoStartTimer: 30

gui:
  name: "&6Red Light Settings"
  size: 45
  items:
    timeLimit:
      slot: 11
      name: "&a⏰ Time Limit"
      lore:
        - "&7Current: &f{timeLimit} seconds"
        - "&7Click to change"
    minPlayers:
      slot: 13
      name: "&b👥 Minimum Players"
      lore:
        - "&b⚙ Minimum Players Required"
        - ""
        - "&bCurrent Value: &f{minPlayers}"
        - ""
        - "&aLeft Click: &f+1 player"
        - "&cRight Click: &f-1 player"
        - "&aShift + Left: &f+5 players"
        - "&cShift + Right: &f-5 players"
    autoStartTimer:
      slot: 15
      name: "&e⏱ Auto-Start Timer"
      lore:
        - "&e⚙ Auto-Start Timer Settings"
        - ""
        - "&eCurrent Value: &f{autoStartTimer} seconds"
        - ""
        - "&aLeft Click: &f+5 seconds"
        - "&cRight Click: &f-5 seconds"
        - "&aShift + Left: &f+30 seconds"
        - "&cShift + Right: &f-30 seconds"
```

---

## Commands

### Basic Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/tgsg` or `/sg` | Show help menu | - |
| `/tgsg reload` | Reload plugin configuration | `tgsg.admin` |
| `/tgsg list` | List all arenas | `tgsg.admin` |
| `/tgsg create <name> <type>` | Create a new arena | `tgsg.admin` |
| `/tgsg delete <name>` | Delete an arena | `tgsg.admin` |

### Arena Setup Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/tgsg <arena> setpos1` | Set arena corner 1 | `tgsg.admin` |
| `/tgsg <arena> setpos2` | Set arena corner 2 | `tgsg.admin` |
| `/tgsg <arena> setstart1` | Set start area corner 1 | `tgsg.admin` |
| `/tgsg <arena> setstart2` | Set start area corner 2 | `tgsg.admin` |
| `/tgsg <arena> setwin1` | Set win zone corner 1 | `tgsg.admin` |
| `/tgsg <arena> setwin2` | Set win zone corner 2 | `tgsg.admin` |
| `/tgsg <arena> setlobby` | Set lobby spawn point | `tgsg.admin` |
| `/tgsg <arena> setspec` | Set spectator spawn point | `tgsg.admin` |

### Arena Management Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/tgsg <arena> edit` | Open arena settings GUI | `tgsg.admin` |
| `/tgsg <arena> save` | Save and exit edit mode | `tgsg.admin` |
| `/tgsg <arena> cancel` | Exit edit mode without saving | `tgsg.admin` |
| `/tgsg <arena> enablebarrier` | Enable barrier blocks | `tgsg.admin` |
| `/tgsg <arena> disablebarrier` | Disable barrier blocks | `tgsg.admin` |

### Game Control Commands

| Command | Description | Permission |
|---------|-------------|------------|
| `/tgsg <arena> start` | Start the game | `tgsg.admin` |
| `/tgsg <arena> stop` | Stop the game | `tgsg.admin` |
| `/tgsg <arena> join` | Join an arena | - |

---

## Permissions

- `tgsg.admin` - Access to all admin commands and arena setup
- No special permission required for players to join games

---

## Red Light Green Light Game

### How It Works

1. **Player Joining**: Players join the arena and wait in the lobby
2. **Auto-Start**: Game automatically starts when minimum players join (configurable)
3. **Countdown**: 5-second countdown without teleportation (players stay in current positions)
4. **Green Light Phase**: Players can move freely toward the win zone (4-10 seconds)
5. **Red Light Phase**: Players must freeze completely (4-10 seconds)
6. **Movement Detection**: Players who move during red light are eliminated (0.15 block threshold)
7. **Win Condition**: Players who reach the win zone are declared winners
8. **Time Limit**: Game ends after the configured time limit

### Game Mechanics

#### Countdown System (v1.2 Improvement)
- Players are **not** teleported during the 5-second countdown
- Players start the game from their current position when countdown ends
- This prevents unwanted teleportation and maintains player positioning

#### Movement Detection
- **Threshold**: 0.15 blocks (very sensitive)
- **Grace Period**: 10 ticks (0.5 seconds) after red light starts
- **Detection**: Tracks X, Y, and Z coordinate changes
- **Elimination**: Instant elimination for movement during red light

#### Auto-Start Feature
- **Minimum Players**: Configurable per arena (default: 2)
- **Auto-Start Timer**: Configurable countdown when minimum players reached
- **Manual Override**: Admins can still manually start games

### Elimination Rules

- Moving during red light = Instant elimination
- Leaving arena bounds = Instant elimination
- Disconnecting = Automatic elimination
- Eliminated players become spectators

### Spectator Mode

- Eliminated and winning players enter spectator mode
- Can freely fly within arena bounds
- Cannot interfere with active players
- Must stay within arena boundaries

---

## Future Minigames (Planned)

- Glass Bridge
- Tug of War
- Marbles
- Honeycomb/Dalgona Candy
- And more!

---

## Support & Credits

**Developed by:** Techinpoint Gamerz (TG)
**Version:** 1.2
**Minecraft Version:** 1.21.1+
**Server Software:** Paper (recommended), Spigot compatible
**Java Requirement:** Java 21+

For support, please contact Techinpoint Gamerz.

---

## License

This plugin is proprietary software. All rights reserved by Techinpoint Gamerz.

---

## Changelog

### Version 1.1 (Latest)
- **Fixed**: Teleportation bug during countdown - players no longer teleported during 5-second countdown
- **Enhanced**: GUI design with improved lore, Unicode symbols, and color-coded information
- **Added**: Arena setup completion notifications when all positions are configured
- **Upgraded**: Migrated to Paper API with Java 21 support for better performance
- **Improved**: Minimum players and auto-start timer GUI with detailed click actions
- **Enhanced**: Professional polish throughout the plugin interface

### Version 1.0 (Initial Release)
- Red Light Green Light minigame implementation
- Multi-arena support
- GUI configuration system
- Barrier management
- Spectator mode
- Disconnect handling
- BossBar integration
- Sound effects
