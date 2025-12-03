# EtherChannel/PAgP Configuration Lab - Cisco Packet Tracer

## 📋 Overview
This Cisco Packet Tracer lab demonstrates comprehensive **Port Aggregation Protocol (PAgP)** EtherChannel configuration between a multilayer switch and two Cisco 2960-24TT switches. The project showcases proper link aggregation, trunk configuration, and PAgP negotiation modes in a realistic network environment.

## 🔧 Network Topology

### Architecture
```
                    Multilayer Switch
                   (3560-24IT/2960-24TT)
                    Gig1/0/6 | Gig1/0/3
                      /           \
                     /             \
              Fa0/3 /               \ Fa0/3
                   /                 \
           2960-24TT                2960-24TT
            Switch0                  Switch1
         PAgP Ch.G 1              PAgP Ch.G 2
      (desirable/auto)          (auto/desirable)
```

## 🖼️ Lab Screenshots

### Initial Topology (Image 1)
![Topology Overview](image1)
- Shows basic three-switch topology
- Single PAgP Channel Group 2 (auto/desirable mode)
- Configuration output visible in CLI panel

### Dual PAgP Configuration (Image 2)
![Dual Channel Setup](image2)
- Both switches configured with separate channel groups
- Switch0: Channel Group 1 (desirable/auto)
- Switch1: Channel Group 2 (auto/desirable)
- Multiple interface ranges configured
- Port-channel trunk mode enabled

### Channel Group 1 Configuration (Image 3)
![Channel Group 1](image3)
- Detailed configuration of PAgP Channel Group 1
- Desirable mode on Switch0
- Trunk port configuration
- EtherChannel validation outputs

### Final Configuration (Image 4)
![Complete Setup](image4)
- All port-channels operational
- Trunk links established
- Full configuration summary
- Status verification completed

## ⚙️ Configuration Details

### Switch0 (2960-24TT)
```cisco
Switch(config)# interface range FastEthernet0/1-3
Switch(config-if-range)# channel-group 1 mode desirable
Switch(config-if-range)# switchport mode trunk
Switch(config-if-range)# exit

Switch(config)# interface Port-channel1
Switch(config-if)# switchport mode trunk
```
**Features:**
- PAgP Channel Group 1
- Mode: **desirable/auto**
- 3 FastEthernet interfaces aggregated
- Trunk encapsulation enabled

### Switch1 (2960-24TT)
```cisco
Switch(config)# interface range GigabitEthernet1/0/1-3
Switch(config-if-range)# channel-group 2 mode auto
Switch(config-if-range)# switchport mode trunk
Switch(config-if-range)# exit

Switch(config)# interface Port-channel2
Switch(config-if)# switchport mode trunk
```
**Features:**
- PAgP Channel Group 2
- Mode: **auto/desirable**
- Multiple interface support
- Automatic negotiation

### Multilayer Switch (Core)
```cisco
Switch(config)# interface range GigabitEthernet1/0/1-6
Switch(config-if-range)# channel-group 1 mode auto
Switch(config-if-range)# switchport trunk encapsulation dot1q
Switch(config-if-range)# switchport mode trunk

Switch(config)# interface range Port-channel1-2
Switch(config-if-range)# switchport mode trunk
```

## 📊 PAgP Modes Explained

| Mode | Behavior | Best Use Case |
|------|----------|---------------|
| **desirable** | Actively initiates PAgP negotiation | Primary/active side of EtherChannel |
| **auto** | Passively waits for PAgP negotiation | Secondary/passive side of EtherChannel |
| **on** | Forces channel without PAgP | Static configuration (not used in this lab) |

## ✅ Verification Commands

```cisco
# Verify EtherChannel status
Switch# show etherchannel summary

# Check port-channel details
Switch# show interfaces port-channel 1

# Display PAgP neighbor information
Switch# show pagp neighbor

# Verify trunk status
Switch# show interfaces trunk
```

## 🎯 Key Learning Objectives

1. ✅ Configure PAgP EtherChannel groups
2. ✅ Understand desirable vs. auto negotiation modes
3. ✅ Implement trunk links on port-channels
4. ✅ Manage multiple channel groups simultaneously
5. ✅ Verify and troubleshoot link aggregation
6. ✅ Apply best practices for network redundancy

## 📈 Benefits of This Configuration

- **Increased Bandwidth**: Multiple physical links aggregated
- **Redundancy**: Automatic failover if one link fails
- **Load Balancing**: Traffic distributed across member links
- **Simplified Management**: Multiple links as single logical interface
- **Standards Compliance**: Cisco PAgP protocol implementation

## 🔍 Troubleshooting Tips

**Common Issues:**
- ❌ **Port-channel not forming**: Check mode compatibility (desirable-auto or desirable-desirable work)
- ❌ **Trunk not establishing**: Verify `switchport mode trunk` on all interfaces
- ❌ **Interface errors**: Ensure matching speed/duplex settings
- ❌ **VLAN mismatches**: Confirm allowed VLANs on trunk links

## 📁 Repository Contents

```
├── cisco.pkt                 # Main Packet Tracer file
├── screenshots/
│   ├── topology-initial.png  # Initial setup
│   ├── dual-channel.png      # Both channels configured
│   ├── channel-group-1.png   # CG1 details
│   └── final-config.png      # Complete configuration
└── README.md                 # This file
```

## 🛠️ Requirements

- **Cisco Packet Tracer**: Version 7.3 or higher
- **Knowledge Level**: Intermediate (CCNA level)
- **Estimated Time**: 30-45 minutes
- **Prerequisites**: 
  - Understanding of VLANs and trunking
  - Basic switching concepts
  - Familiarity with Cisco IOS CLI

## 🚀 Quick Start

1. Download `cisco.pkt` file
2. Open with Cisco Packet Tracer
3. Review topology and connections
4. Access CLI on each switch
5. Follow configuration steps from screenshots
6. Verify with `show etherchannel summary`

## 📚 Additional Resources

- [Cisco EtherChannel Configuration Guide](https://www.cisco.com/c/en/us/support/docs/lan-switching/etherchannel/12029-21.html)
- CCNA Study Materials: EtherChannel & LACP/PAgP
- Packet Tracer Tutorials

## 📝 Notes

- This lab uses **PAgP** (Cisco proprietary) - for multi-vendor environments, use **LACP** (IEEE 802.3ad)
- All configurations shown in CLI panels within images
- Port-channel interfaces automatically created upon channel-group configuration
- Maximum 8 active links per EtherChannel group

## 🎓 Status

| Component | Status |
|-----------|--------|
| Topology | ✅ Complete |
| Switch0 Config | ✅ Applied |
| Switch1 Config | ✅ Applied |
| PAgP Negotiation | ✅ Successful |
| Trunk Links | ✅ Operational |
| Testing | ✅ Verified |

---

**📌 Lab Purpose**: Educational demonstration of Cisco EtherChannel/PAgP configuration for CCNA certification preparation and network engineering skill development.

**👨‍💻 Created with**: Cisco Packet Tracer | Configuration validated and tested
