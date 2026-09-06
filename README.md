# Mountain Mesh Node Setup Guide

This guide's original text, examples, HTML, and CSS are licensed under the [MIT License](LICENSE). Images, logos, third-party material, and linked firmware or services are not included in this grant.

Welcome to the step-by-step guide on how to create and add a Meshtastic node to the [Mountain Mesh](https://mtnme.sh/) network. Mountain Mesh is a community group building a resilient, decentralized, and community-owned communications network in the southern Appalachian Mountains using the open-source Meshtastic platform.

This guide will walk you through the entire process, from selecting the right hardware to configuring your node for the Mountain Mesh network.

## Table of Contents

1. [Introduction to Mountain Mesh](#introduction-to-mountain-mesh)
2. [Hardware Selection](#hardware-selection)
3. [Flashing Firmware](#flashing-firmware)
4. [Initial Configuration](#initial-configuration)
5. [Mountain Mesh Specific Configuration](#mountain-mesh-specific-configuration)
6. [Resources and Community](#resources-and-community)

## Introduction to Mountain Mesh

Mountain Mesh operates in the 915 MHz ISM band, which is legal for unlicensed use in the United States. The community is focused on deploying the Meshtastic platform, an open-source, long-range, low-power mesh networking solution that uses inexpensive, off-the-shelf LoRa radios.

**Important Note:** As of October 1, 2025, Mountain Mesh migrated their network to the **MediumFast** modem preset to reduce message collisions and network congestion.

## Hardware Selection

Before you begin, you need to select a Meshtastic-compatible device. There are several options depending on your needs and technical expertise.

### Recommended Devices for Beginners

For those new to Meshtastic, plug-and-play devices are highly recommended.

*   **Heltec V3:** A very affordable and popular bare board option. It requires a case and battery but is a great starting point.
*   **LILYGO T-Echo:** An all-in-one unit with an E-Ink screen, GPS, and battery in an injection-molded case. It uses the power-efficient nRF52 chip.
*   **RAK Wireless WisBlock:** A modular hardware system that offers excellent battery life and flexibility for adding sensors. RAK offers starter kits that are easy to assemble.

### Mountain Mesh Custom Hardware

The Mountain Mesh community has also designed custom hardware:

*   **MeshToad:** A Meshtastic-compatible LoRa radio designed to turn any Linux computer into a Meshtastic node via USB-C. It features a 1W TX and an LNA for increased RX sensitivity.

## Flashing Firmware

Once you have your hardware, you need to install the Meshtastic firmware.

1.  **Connect your device:** Use a high-quality USB data cable to connect your device to your computer. Ensure the cable supports data transfer, not just charging.
2.  **Attach the antenna:** **Never power on the radio without attaching an antenna**, as doing so could damage the radio chip.
3.  **Use the Web Flasher:** The easiest way to flash firmware is using the official [Meshtastic Web Flasher](https://flasher.meshtastic.org/). This requires a Chromium-based browser (like Chrome or Edge).
4.  **Select your device:** Follow the on-screen instructions to select your specific device model and the latest stable firmware version.
5.  **Flash:** Click the flash button and wait for the process to complete.

## Initial Configuration

After flashing, you need to perform the initial setup.

1.  **Download the App:** Download the Meshtastic app on your iOS or Android device.
2.  **Pair via Bluetooth:** Open the app and pair it with your Meshtastic node via Bluetooth.
3.  **Set Region:** The most critical initial step is setting your LoRa region. For the United States (and Mountain Mesh), set the region to **US (902.0 - 928.0 MHz)**.

## Mountain Mesh Specific Configuration

To join the Mountain Mesh network, you must configure your node with their specific settings. These settings prioritize network stability by reducing unnecessary "chattiness" on the shared bandwidth.

### 1. Modem Preset and Frequency

Mountain Mesh uses the **MediumFast** preset.

*   **Modem Preset:** `MediumFast`
*   **Frequency Slot:** `45` (913.125 MHz)
*   **Hop Limit:** `5` (Do not set higher than 6)

### 2. Channel Configuration

*   **Primary Channel (0):** Name it `MediumFast` with the default PSK of `AQ==`.
*   **Secondary Channel (1) (Optional):** Name it `LongFast` with the default PSK of `AQ==`. This allows you to receive messages from bridged nodes.

### 3. Role and Telemetry Settings

Your settings should vary based on how you use your node.

#### Personal Mobile Nodes (Everyday Carry)

*   **Device Role:** `CLIENT` or `CLIENT_MUTE`
*   **NodeInfo Interval:** `10800` (3 hours)
*   **Smart Position:** `True` (Smart Interval: 15 mins, Smart Distance: 1 km)
*   **Broadcast Interval:** `10800` (3 hours)
*   **Ignore MQTT:** `True`
*   **OK to MQTT:** `True`

#### Personal/Local Infrastructure (Home Base Stations)

*   **Device Role:** `CLIENT` or `CLIENT_BASE`
*   **NodeInfo Interval:** `21600` (6 hours)
*   **Hop Limit:** `3`
*   **Smart Position:** `False`
*   **Fixed Position:** `True` (Set manually)
*   **Broadcast Interval:** `21600` (6 hours)
*   **Ignore MQTT:** `True`
*   **OK to MQTT:** `True`

### Auto-Configuration

Mountain Mesh provides an auto-configuration URL and QR code on their [MediumFast Migration page](https://mtnme.sh/mediumfast/). Scanning this QR code with your phone's camera while the Meshtastic app is open will automatically apply the basic MediumFast settings.

## Resources and Community

*   **Mountain Mesh Website:** [https://mtnme.sh/](https://mtnme.sh/)
*   **Mountain Mesh Discord:** Join their active Discord community for support, events, and meetups. Links are available on their website.
*   **Live Map:** View the network in real-time using their [MeshView instance](https://view.mtnme.sh/).
*   **Official Meshtastic Documentation:** [https://meshtastic.org/docs/](https://meshtastic.org/docs/)

---
*This guide was created to help new users easily join the Mountain Mesh network. For the most up-to-date information, always refer to the official Mountain Mesh website.*
