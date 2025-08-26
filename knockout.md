# TLE Enhanced Knockout System

**Realistic unarmed combat knockout system for RedM with multi-framework support and progressive stages.**

![Version](https://img.shields.io/badge/version-2.0.0-blue)
![Framework](https://img.shields.io/badge/framework-Multi--Framework-green)
![Game](https://img.shields.io/badge/game-RedM-red)

## 🌟 Features

### Progressive Knockout System
- **3-Stage Progression**: Dazed → Stunned → Full Knockout
- **Realistic Health Thresholds**: Each stage triggers at different health levels
- **Dynamic Recovery**: Some stages allow natural recovery

### Advanced Visual Effects  
- **REDMIST Effect**: Signature white/black visual during knockout
- **Camera Shake**: Progressive intensity based on damage
- **Screen Flash**: Impact feedback with customizable colors
- **Gradual Transitions**: Smooth effect fade-ins and fade-outs

### Multi-Framework Support
- **RSGCore** - Full integration with notification system
- **LXRCore** - Native support with custom configurations  
- **QBRCore** - Complete compatibility
- **VORP** - Event-based integration
- **Standalone** - Works without any framework

### Realistic Mechanics
- **Reputation System**: Build fighting toughness over time
- **Witness System**: NPCs and law enforcement may respond
- **Cooldown Protection**: Prevents knockout spam
- **Anti-Abuse**: Situational protections (no KO while falling, etc.)

### Recovery Features
- **Passive Regeneration**: Gradual health recovery during knockout
- **Immunity Periods**: Temporary protection after recovery
- **Progressive Control**: Gradual return of player controls

## 📋 Requirements

- **RedM Server** (Latest build recommended)
- **Framework**: RSGCore, LXRCore, QBRCore, VORP, or Standalone
- **ox_lib** (Optional - for enhanced UI features)

## 🚀 Installation

### Quick Install
1. **Download** the resource and extract to your `resources` folder
2. **Add to server.cfg**:
```bash
ensure rsg-core          # or your framework
ensure tle_knockout_enhanced
```
3. **Configure** `config.lua` to match your server setup
4. **Restart** your server

### Framework-Specific Setup

#### RSGCore
```bash
ensure rsg-core
ensure tle_knockout_enhanced
```

#### LXRCore  
```bash
ensure lxr-core
ensure tle_knockout_enhanced
```

#### VORP
```bash
ensure vorp_core
ensure tle_knockout_enhanced
```

## ⚙️ Configuration

### Basic Settings
```lua
Config.RequireUnarmedOnly = true        -- Only fists trigger KO
Config.KnockoutHealthBelow = 145        -- Health threshold for full KO  
Config.KODurationSeconds = 15           -- Knockout duration
```

### Knockout Stages
Configure the 3-stage progression system:
```lua
Config.KnockoutStages = {
    {
        name = "dazed",
        healthRange = {160, 180},
        effects = {
            timecycle = "spectator5",
            cameraShake = {name = "SMALL_EXPLOSION_SHAKE", amplitude = 0.3},
            movementSpeed = 0.8,
        },
        duration = 3,
        canRecover = true
    },
    -- ... more stages
}
```

### Visual Effects
```lua
Config.Effects = {
    useTimecycleEffects = true,
    useCameraShake = true,
    flashEffect = {
        enabled = true,
        duration = 200,
        color = {255, 255, 255, 180}
    }
}
```

### Framework Notifications
```lua
Config.Framework = {
    notifications = {
        rsg = {
            resource = "rsg-core",
            export = "Notify",
            args = {"%s", "inform", 5000}
        }
        -- ... other frameworks
    }
}
```

## 🎮 How It Works

### Stage 1: Dazed (180-160 HP)
- Light visual effects (spectator5 timecycle)
- Slight movement speed reduction
- Can recover naturally after 3 seconds
- Maintains full control

### Stage 2: Stunned (160-145 HP)  
- Stronger visual effects (spectator3 timecycle)
- Attack and aim controls disabled
- Reduced movement speed
- Can recover after 5 seconds

### Stage 3: Full Knockout (<145 HP)
- REDMIST visual effect (signature white/black)
- Full ragdoll state
- All controls disabled
- Lasts full knockout duration (configurable)

## 🔧 Advanced Features

### Reputation System
Players build "Fighting Toughness" over time:
- Gain experience from each knockout survived
- Higher reputation = harder to knockout
- Gradual decay when not fighting

### Witness System
NPCs may witness fights and alert law enforcement:
- Base chance: 15% in wilderness
- Town chance: 35% in populated areas  
- May result in fines or law response

### Cooldown Protection
- 3-minute cooldown between potential knockouts
- 30-second immunity period after recovery
- Prevents knockout griefing

## 🐛 Troubleshooting

### Common Issues

**"No such export Notify in resource"**
- Ensure your framework is loaded before knockout script
- Check framework notification configuration in config.lua

**Players stuck in knockout**  
- Server-side watchdog automatically recovers stuck players
- Maximum knockout time enforced (60 seconds default)

**Black screen issues**
- REDMIST effect keeps screen visible unlike fade-to-black
- Gradual recovery system prevents jarring transitions

**Framework not detected**
- Verify framework resource name in Config.Framework.priority
- Check server console for framework detection logs

### Debug Mode
Enable debugging to troubleshoot issues:
```lua
Config.Debug = true
```

Then check console for detailed logging:
- Framework detection status
- Effect application/removal
- Player state changes
- Error messages with context

## 🎯 Performance

### Optimizations
- **Adaptive Update Rates**: Faster updates only during combat
- **Efficient State Management**: Minimal memory footprint
- **Smart Effect Cleanup**: Prevents lingering visual effects
- **Network Optimization**: Server sync only when needed

### Resource Usage
- **Memory**: ~2-5MB depending on configuration
- **CPU**: <0.01ms per frame (idle), ~0.05ms (active combat)
- **Network**: Minimal - sync only on knockout events

## 🤝 Support

### Documentation
- In-line code comments for developers
- Comprehensive configuration examples
- Framework-specific setup guides

### Community  
- GitHub issues for bug reports
- Discord support through The Lux Empire
- Regular updates and improvements

### Professional Support
For custom modifications or enterprise support:
- **Website**: davidio.dev
- **GitHub**: github.com/iBoss21
- **Store**: theluxempire.tebex.io

## 📄 License

MIT License - see LICENSE file for details

## 📈 Changelog

### v2.0.0 (Current)
- Complete rewrite with progressive knockout stages
- Multi-framework support (RSGCore, LXRCore, QBRCore, VORP)
- Advanced visual effects system
- Reputation and witness systems
- Enhanced multiplayer synchronization
- Comprehensive configuration system

### v1.1.0
- Added basic visual effects
- Framework detection improvements
- Bug fixes for multiplayer sync

### v1.0.0
- Initial release
- Basic knockout mechanics
- Single framework support

---

**Made with ❤️ by The Lux Empire**  
*Elevating RedM roleplay experiences*
