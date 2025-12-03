# EtherChannel/PAgP Configuration Lab - Cisco Packet Tracer

## Overview
This Cisco Packet Tracer lab demonstrates the configuration of Port Aggregation Protocol (PAgP) EtherChannel between two Cisco 2960-24TT switches. The lab showcases both automatic and desirable PAgP modes with trunk configuration.

## Network Topology
- **Multilayer Switch**: Central device with GigabitEthernet interfaces
- **Switch0 (2960-24TT)**: Connected via FastEthernet0/3, PAgP Channel Group 1 (desirable/auto mode)
- **Switch1 (2960-24TT)**: Connected via FastEthernet0/3, PAgP Channel Group 2 (auto/desirable mode)

## Configuration Highlights

### EtherChannel Features
- **PAgP Protocol**: Cisco proprietary link aggregation protocol
- **Channel Groups**: Two separate port-channel groups configured
- **Modes**: 
  - Channel Group 1: desirable/auto
  - Channel Group 2: auto/desirable
- **Trunk Configuration**: All port-channels configured as trunk links

### Switch Configurations

#### Switch0
```
interface range FastEthernet0/1-3
 channel-group 1 mode desirable
 switchport mode trunk
```

#### Switch1
```
interface range GigabitEthernet1/0/1-3
 channel-group 1 mode auto
 switchport mode trunk

interface Port-channel1
 switchport mode trunk
```

#### Multilayer Switch
- Multiple port-channels configured with auto/desirable modes
- Trunk mode enabled on aggregated links
- Interface range configurations for efficient setup

## Key Learning Points
1. PAgP channel group configuration
2. Trunk mode setup on EtherChannels
3. Automatic vs. desirable PAgP negotiation
4. Multiple port-channel management
5. Link aggregation for redundancy and bandwidth

## Lab Files
- `cisco.pkt` - Main Packet Tracer simulation file
- Configuration snapshots showing CLI outputs and status

## Requirements
- Cisco Packet Tracer 7.x or higher
- Basic understanding of Layer 2 switching
- Knowledge of trunk and EtherChannel concepts

## Status
✅ All configurations applied successfully  
✅ Port-channels operational  
✅ Trunk links established  
✅ PAgP negotiation complete

---
*Lab created for educational purposes to demonstrate Cisco EtherChannel/PAgP configuration and best practices.*
