# SonicWall Gen 6 and Gen 7 to Gen 8 Migration

A step-by-step conversion guide and firmware compatibility workaround for migrating SonicWall Gen 6 and Gen 7 configurations to Gen 8 hardware.

# Overview

This guide covers the process of converting a Gen 6 or Gen 7 SonicWall configuration to a Gen 8 appliance, including a workaround for older Gen 6 devices running outdated or unsupported firmware.

This process was used to migrate a SonicWall TZ300 (Gen 6) configuration to a TZ280 (Gen 8) using a TZ270 (Gen 7) configuration as an intermediate step.

# Phase 1: Export the Original Configuration

1. Log into the original SonicWall firewall.
2. Navigate to Device > Settings > Firmware and Settings. (Navigation may vary depending on firmware version.)
3. Click Export Settings and save the configuration file to your computer.
4. Keep a backup of the original configuration in case you need to restore it.

# Phase 2: Workaround for Older Gen 6 Configurations

Skip this phase if you already have a compatible Gen 7 configuration.

1. Navigate to the SonicWall Migration Tool: https://migratetool.global.sonicwall.com/
2. Follow the prompts and upload your exported Gen 6 configuration.
3. When selecting the target device, choose a compatible Gen 7 model.
4. Complete the conversion process.
5. Download the converted Gen 7 configuration file.

Example: A TZ300 (Gen 6) configuration can be converted to a TZ270 (Gen 7), which can then be converted to a TZ280 (Gen 8).

NOTE: This workaround was successful during my migration. Compatibility may vary depending on the appliance models and firmware versions.

# Phase 3: Convert Gen 7 to Gen 8

1. Power on your new Gen 8 SonicWall firewall.
2. Connect your computer directly to the firewall's LAN interface using an Ethernet cable.
3. Open your computer's Ethernet adapter settings and manually configure a static IPv4 address.
   - Computer IP: 192.168.168.100
   - Subnet Mask: 255.255.255.0
   - SonicWall Default IP: 192.168.168.168
4. Open a web browser and navigate to https://192.168.168.168
5. Log into the firewall and complete the initial setup.
6. Register the new device.
7. Navigate to Firmware and Settings.
8. Use the built-in migration tool to convert the Gen 7 configuration to the Gen 8 format.
9. Import the converted configuration.
10. Allow the firewall to apply the configuration and reboot.

NOTE: After importing the configuration, the firewall may inherit the original device's management IP address and login credentials.

If you lose access to the firewall, you may need to change your computer's static IP address to match the subnet used by the imported configuration.

This can make it appear that the firewall is not responding even though the configuration was successfully imported.

# Phase 4: Configuration Verification

1. Once logged into the new SonicWall, verify that all settings transferred successfully.
2. Compare the new firewall's configuration against the original firewall.
3. Verify the following settings:
   - WAN and LAN interfaces
   - VLAN configurations
   - Firewall access rules
   - NAT policies
   - VPN tunnels
   - DHCP settings
   - Address and service objects
   - Routing configurations
   - User authentication and SSO settings
   - Security services and licensing
4. Verify that the correct interfaces are assigned to the appropriate networks.
5. Manually reconfigure any settings that did not transfer correctly.

NOTE: VPN tunnels, VLAN configurations, and authentication settings may not transfer completely and could require manual configuration.


# References

SonicWall Migration Tool:
https://migratetool.global.sonicwall.com/

SonicWall Technical Documentation:
https://www.sonicwall.com/support/technical-documentation

# Disclaimer

This guide documents a migration process that worked for a SonicWall TZ300 to TZ280 upgrade. Other SonicWall models or firmware versions may require different steps.

Always back up the original configuration, verify compatibility, and test the new firewall before deploying it into a production environment.

Always back up the original configuration, verify compatibility with SonicWall documentation, and test the new firewall before deploying it into a production environment.
