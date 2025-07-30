# Prison Escape Server Setup Guide

**Complete Guide to Setting Up the Ultimate Prison Escape Minecraft Server**

Transform your Minecraft server into an exciting prison escape destination! This comprehensive guide walks you through every step of setting up and configuring the Prison Escape plugin for optimal player experience.

## 🎯 Why Choose Prison Escape for Your Server?

Prison Escape is more than just another minigame - it's a complete multiplayer experience that will keep players engaged and coming back for more.

### Benefits for Server Owners:
- **High Player Retention**: Engaging gameplay that encourages repeat visits
- **Community Building**: Team-based gameplay fosters player interaction
- **Easy Setup**: Simple installation and configuration process
- **Customizable**: Adaptable to different server themes and styles
- **Regular Updates**: Active development and community support

## 🛠️ System Requirements

### Minimum Requirements
- **Minecraft Version**: 1.20 or higher
- **RAM**: 2GB minimum (4GB recommended)
- **CPU**: Dual-core processor
- **Storage**: 1GB free space
- **Plugins**: WorldEdit, Citizens, Multiverse-Core

### Recommended Requirements
- **RAM**: 6GB+ for multiple simultaneous games
- **CPU**: Quad-core processor
- **Storage**: SSD for faster world loading
- **Internet**: Stable connection for multiplayer
- **Plugins**: WorldEdit, Citizens, Multiverse-Core, Vault

## 🚀 Installation Process

### Step 1: Download Required Files
```bash
# Download Prison Escape plugin
wget https://github.com/TiagoFar78/PrisonEscape/releases/latest/download/PrisonEscape.jar

# Download required dependencies
# WorldEdit: https://dev.bukkit.org/projects/worldedit
# Citizens: https://dev.bukkit.org/projects/citizens
# Multiverse-Core: https://dev.bukkit.org/projects/multiverse-core
```

### Step 2: Plugin Installation
1. **Place JAR Files**: Move all downloaded .jar files to your server's `plugins` folder
2. **Start Server**: Launch your Minecraft server
3. **Verify Installation**: Check console for successful plugin loading messages
4. **Generate Config**: The plugin will create default configuration files

### Step 3: World Setup
```bash
# Create prison world
/mv create PrisonEscapeLobby normal
/mv create PrisonEscape normal

# Set world settings
/mv modify set gamemode adventure PrisonEscapeLobby
/mv modify set gamemode adventure PrisonEscape
```

## ⚙️ Configuration Guide

### Basic Configuration (config.yml)
```yaml
# Game Settings
MaxSimultaneousGames: 4          # Maximum concurrent games
MinPlayers: 3                    # Minimum players per game
MaxPlayers: 11                   # Maximum players per game
DaysAmount: 4                    # Game duration in days
DayDuration: 120                 # Day length in seconds
NightDuration: 60                # Night length in seconds

# Team Balance
PrisonersRatio: 0.73             # 73% prisoners
PoliceRatio: 0.27                # 27% guards

# Game Mechanics
StartingBalance: 0               # Starting money
TrapLimit: 2                     # Max traps per guard
CameraLimit: 1                   # Max cameras per guard
HelicopterSpawnDelay: 10         # Helicopter arrival time
```

### Advanced Configuration Options

#### Economy Settings
```yaml
# Item Prices
TrapPrice: 10
SensorPrice: 10
CameraPrice: 10
RadarPrice: 10
EnergyDrinkPrice: 10
SearchPrice: 5
```

#### Game Timing
```yaml
# Phase Durations (in seconds)
WaitingPhaseDuration: 300         # Lobby wait time
FullLobbyWaitDuration: 10         # Quick start when full
FinishedPhaseDuration: 30        # Results display time
DelayBetweenAnnouncements: 30    # Message interval
```

#### Security Settings
```yaml
# Prison Security
SecondsInSolitary: 30            # Solitary confinement time
SoundDetectorRange: 2.5          # Detection radius
TrapDuration: 10                 # Trap effect duration
BlindnessSeconds: 5              # Flashbang duration
RadarDuration: 10                # Radar active time
```

## 🗺️ Map Creation Guide

### Basic Map Requirements
- **Spawn Point**: Designated waiting area
- **Prison Layout**: Cells, yard, facilities
- **Escape Routes**: Multiple path options
- **Security Features**: Camera locations, trap spots
- **Roof Access**: Helicopter landing zone

### Map Creation Process
1. **Design Layout**: Plan your prison structure
2. **Build Prison**: Construct walls, cells, and facilities
3. **Add Details**: Include decorative elements and obstacles
4. **Set Regions**: Define game areas and boundaries
5. **Test Gameplay**: Ensure balanced gameplay

### Example Map Configuration
```yaml
# maps/YourMapName.yml
Name: "Maximum Security Prison"
Description: "High-security facility with advanced systems"
Authors: ["YourName"]
Version: "1.0"

# Spawn Points
PrisonerSpawn: "world,x,y,z,yaw,pitch"
GuardSpawn: "world,x,y,z,yaw,pitch"
WaitingRoom: "world,x,y,z,yaw,pitch"

# Game Areas
Prison: "region1"
Yard: "region2"
Roof: "region3"
Vault: "region4"

# Special Locations
HelicopterPad: "world,x,y,z"
CameraLocations: ["loc1", "loc2", "loc3"]
SoundDetectorSpots: ["spot1", "spot2"]
```

## 👥 Player Management

### Permission Setup
```yaml
# In your permissions plugin (LuckPerms, etc.)
# Basic permissions
prisonescape.player: true
prisonescape.admin: true

# Command permissions
prisonescape.command.join: true
prisonescape.command.leave: true
prisonescape.command.list: true
prisonescape.command.forcestart: op
prisonescape.command.forcestop: op
prisonescape.command.loadmaps: op
```

### Player Commands
- `/prisonescape join [map]` - Join a game
- `/prisonescape leave` - Leave current game
- `/prisonescape list` - Show active games
- `/prisonescape rejoin` - Rejoin disconnected game

### Admin Commands
- `/prisonescape forcestart [gameId]` - Start game immediately
- `/prisonescape forcestop [gameId]` - Stop current game
- `/prisonescape loadmaps` - Reload all maps
- `/prisonescape reload` - Reload configuration

## 🔧 Performance Optimization

### Server Settings
```yaml
# server.properties
view-distance: 8
simulation-distance: 6
network-compression-threshold: 512
max-tick-time: 60000
```

### Plugin Optimization
```yaml
# spigot.yml
max-chunks-per-tick: 10
entity-activation-range:
  animals: 16
  monsters: 24
  raiders: 48
  misc: 8
```

### Memory Management
```bash
# Java startup parameters
java -Xms2G -Xmx4G -XX:+UseG1GC -XX:+ParallelRefProcEnabled \
-XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions \
-XX:+DisableExplicitGC -XX:+AlwaysPreTouch -XX:G1NewSizePercent=30 \
-XX:G1MaxNewSizePercent=40 -XX:G1HeapRegionSize=8M \
-XX:G1ReservePercent=20 -XX:G1HeapWastePercent=5 \
-XX:G1MixedGCCountTarget=4 -XX:InitiatingHeapOccupancyPercent=15 \
-XX:G1MixedGCLiveThresholdPercent=90 -XX:G1RSetUpdatingPauseTimePercent=5 \
-XX:SurvivorRatio=32 -XX:+PerfDisableSharedMem \
-XX:MaxTenuringThreshold=1 -jar paper.jar nogui
```

## 🎨 Customization Options

### Language Customization
```yaml
# languages/english.yml
Scoreboard:
  DisplayName: "&6&lPrison Escape"
  LastLine: "&eYour Server Name"

Items:
  SelectPrisonerTeam:
    Name: "&6Join Prisoner Team"
  SelectPoliceTeam:
    Name: "&9Join Guard Team"

Messages:
  PrisonerGameStart: "&6You are a prisoner! Work together to escape!"
  PoliceGameStart: "&9You are a guard! Stop all escape attempts!"
```

### Custom Items and Crafting
```yaml
# Add custom crafting recipes
CustomRecipes:
  AdvancedLockpick:
    Materials:
      - IronIngot: 3
      - Redstone: 2
    Result: Lockpick
    Experience: 10
```

### Map-Specific Settings
```yaml
# Per-map configuration
MapSettings:
  BricksField:
    DayDuration: 150
    NightDuration: 75
    StartingBalance: 50
    CustomItems: true
```

## 📊 Monitoring and Analytics

### Game Statistics
- Track player participation rates
- Monitor game completion statistics
- Analyze team win/loss ratios
- Measure player retention

### Performance Monitoring
```bash
# Use these commands to monitor performance
/lag
/tps
/timings paste
/spark profiler
```

### Player Feedback
- Set up suggestion systems
- Monitor player chat for feedback
- Create voting systems for map selection
- Implement bug reporting channels

## 🔒 Security and Moderation

### Anti-Cheat Measures
- Install anti-cheat plugins
- Monitor for suspicious behavior
- Set up logging for player actions
- Implement report systems

### Chat Moderation
- Configure chat filters
- Set up moderation tools
- Monitor team communication
- Prevent harassment and toxicity

## 🚀 Launch and Promotion

### Server Launch Checklist
- [ ] All plugins installed and configured
- [ ] Maps tested and balanced
- [ ] Permissions set up correctly
- [ ] Performance optimized
- [ ] Security measures in place
- [ ] Staff team trained
- [ ] Launch announcement prepared

### Promotion Strategies
- Create server listing descriptions
- Set up social media presence
- Record gameplay videos
- Partner with Minecraft content creators
- Run launch events and tournaments

## 📞 Support and Community

### Getting Help
- **GitHub Issues**: Report bugs and request features
- **Discord Community**: Join other server owners
- **Documentation**: Check the wiki for detailed guides
- **Video Tutorials**: Watch setup and gameplay guides

### Contributing to Development
- Fork the repository on GitHub
- Create detailed bug reports
- Suggest new features and improvements
- Submit pull requests for bug fixes

---

**Ready to create the ultimate prison escape experience for your players? Follow this guide and transform your server into a thriving gaming community!**

*Download Prison Escape today and start building the most exciting Minecraft prison adventure!*