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
| `Level` | Percent (per group) | Light level (0–100%) |
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
  - Level control
  - Increment / Decrement buttons

---

## Communication

The plugin communicates with the Helvar router using TCP commands.

### Command Format
