# Q-SYS Plugin – Helvar DALI Router

## Overview

The **Helvar DALI Router Q-SYS Plugin** enables control of Helvar DALI lighting systems directly from a Q-SYS environment.

It provides group-based lighting control, including level adjustment and incremental changes, via a TCP connection to the Helvar router.

This plugin is designed for scalable installations, supporting multiple DALI groups with an intuitive multi-page interface.

---

## Features

- Control Helvar DALI groups over TCP (port `50000`)
- Adjustable number of groups (2–50)
- Direct level control (0–100%)
- Increment / Decrement buttons with press-and-hold support
- Real-time status feedback
- Multi-page UI for large group counts
- Automatic reconnection handling

---

## Plugin Information

| Property | Value |
|----------|------|
| Name | Helvar DALI Router |
| Version | 1.0.0.0 |
| Author | Jens Claerebout |
| Protocol | TCP |
| Default Port | 50000 |

---

## Configuration

### Properties

| Property | Description |
|----------|------------|
| `#Groups` | Number of DALI groups (2–50). Determines UI size and control count |

---

### Control Pins

#### Inputs

| Control | Type | Description |
|--------|------|------------|
| `IP` | Text | IP address of the Helvar DALI Router |
| `GroupNumber` | Integer (per group) | DALI group address |
| `Direct Level` | Percent (per group) | Light level (0–100%) |
| `Fade Time` | Integer (per group) | Fade Time (1-100 sec) |
| `Increment` | Button | Increase level (step +5, hold to repeat) |
| `Decrement` | Button | Decrease level (step -5, hold to repeat) |

#### Outputs

| Control | Type | Description |
|--------|------|------------|
| `Status` | Indicator | Connection/system status |
| `Level` | Percent (per group) | Light level (0–100%) |

---

## UI Layout

### Page 1 – Configuration

- Connection status
- IP address input

### Pages 2+ – Group Control

- Groups are displayed in blocks of 10 per page
- Each group includes:
  - Group number input
  - Direct Level control
  - Fade Time
  - Increment / Decrement buttons

---

## Communication

The plugin communicates with the Helvar router using TCP commands.

### Command Format
V:1,C:13,G:<group>,L:<level>,F:<fade>#

### Example
V:1,C:13,G:5,L:75,F:300#

This sets:

- Group: `5`
- Level: `75%`
- Fade: `3s`

---

## Behavior

### Increment / Decrement

- Step size: **5%**
- Hold button → repeats every **0.2 seconds**

### Level Control

- Direct changes send immediate commands with set fade time to all devices in group.

### Connection Handling

- Automatically connects on:
  - Plugin initialization
  - IP change
- Handles:
  - Reconnects
  - Timeouts
  - Errors

---

## Installation

1. Place the plugin in your Q-SYS plugin directory or deploy via Designer
2. Add the plugin to your design
3. Configure:
   - Set IP address of Helvar router
   - Set Number of groups in properties
   - Set HelvarNet Version (default: V1)
   - Enter Group numbers as configured in Helvar Designer
4. Deploy to Core

---

## Notes

- Ensure the Helvar router is reachable on port `50000`
- Group numbers must match your Helvar configuration
- No authentication is currently implemented

---

## Known Limitations

- No feedback parsing from Helvar, HelvarNet does not support group level feedback
- No automatic group discovery
- No scene control (yet)

---

## Future Improvements

- Level feedback parsing
- Scene control support
- Group naming
- Authentication support (if required by Helvar)
- UI enhancements

---

## License

MIT License

---

## Author

**Jens Claerebout**
