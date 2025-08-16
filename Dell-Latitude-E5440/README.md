# Dell Latitude E5440 Laptop - Hackintosh EFI

This folder contains the OpenCore EFI configuration for the Dell Latitude E5440 laptop.

## 🖥️ Hardware Specifications

| Component | Details |
|-----------|---------|
| **Model** | Dell Latitude E5440 Business Laptop |
| **CPU** | Intel Core i5-4200U (2C/4T, 1.6GHz base, 2.6GHz boost, Haswell, 22nm) |
| **GPU** | Intel HD Graphics 4400 (integrated, no dedicated GPU) |
| **RAM** | DDR3L-1600 (upgradeable, varies by configuration) |
| **Storage** | Various configurations (HDD/SSD) |
| **Audio** | Intel HD Audio / Realtek Audio Codec |
| **Ethernet** | Intel Ethernet Connection I217-LM Gigabit |
| **WiFi/BT** | Intel Wireless-N/AC + Bluetooth (not working) |
| **Display** | 14" HD/FHD LCD (1366x768 or 1920x1080) |

## 🍎 macOS Compatibility

| macOS Version | Status | Notes |
|---------------|--------|-------|
| macOS Monterey (12.x) | ✅ Supported | Latest compatible version for Haswell architecture |
| macOS Big Sur (11.x) | ✅ Supported | Full compatibility with proper patches |
| macOS Catalina (10.15.x) | ✅ Supported | Native support, recommended for stability |
| macOS Mojave (10.14.x) | ✅ Supported | Excellent compatibility |

> **Note**: macOS Ventura (13.x) and newer versions have dropped support for Haswell processors (4th gen Intel). macOS Monterey is the latest officially supported version.

## 🔧 OpenCore Information

- **OpenCore Version**: Latest stable release
- **SMBIOS**: MacBookPro11,1 (recommended for Haswell laptop)
- **Configuration Date**: August 16, 2025
- **Target macOS**: macOS Monterey 12.7.x
- **Architecture**: x64 (64-bit)

## ✅ What's Working

- [x] Boot into macOS Monterey
- [x] Audio (internal speakers and integrated microphone)
- [x] Ethernet (Intel I217-LM gigabit connection)
- [x] USB 2.0 and USB 3.0 ports
- [x] Sleep/Wake functionality
- [x] Webcam (built-in HD webcam)
- [x] Touchpad and keyboard (full functionality)
- [x] BD PROCHOT (fixed using .efi driver at boot)
- [x] Graphics acceleration (Intel HD 4400 basic functionality)
- [x] Battery percentage and power management
- [x] Hardware acceleration for video playback

## ❌ What's Not Working

- [x] Display brightness control (no brightness adjustment)
- [x] WiFi (Intel Wireless-N/AC not supported)
- [x] Bluetooth (Intel Bluetooth not working)
- [x] AirDrop/Handoff (due to lack of compatible WiFi/BT)
- [x] macOS Ventura and newer (Haswell limitation)

## 🔧 Current Status

**Mostly Functional**: This EFI configuration is stable and suitable for daily use. macOS Monterey is successfully installed with most hardware features working properly.

**Known Limitations**: Main issues are WiFi/Bluetooth compatibility and brightness control. Consider using USB WiFi adapters for wireless connectivity.

## ⚙️ BIOS/UEFI Settings

### Enable:
- [x] UEFI Boot Mode
- [x] AHCI for SATA drives
- [x] USB 3.0 Support
- [x] Hyper-Threading
- [x] Execute Disable Bit
- [x] Intel VT-x (Hardware Virtualization)

### Disable:
- [x] Secure Boot
- [x] Fast Boot
- [x] CSM/Legacy Boot Support
- [x] Intel SGX (Software Guard Extensions)
- [x] Wake on LAN (to prevent sleep issues)
- [x] USB Legacy Support (if causing boot issues)

> **Dell BIOS Note**: Dell BIOS interfaces are typically more comprehensive than HP. Most settings should be available in Advanced or Security sections.

## 📦 Installation Instructions

### Prerequisites
1. USB drive (8GB or larger)
2. macOS Monterey installer
3. [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) or [ProperTree](https://github.com/corpnewt/ProperTree)

### Steps
1. **Prepare USB Installer**
   ```bash
   # Use createinstallmedia or tools like gibMacOS
   sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
   ```

2. **Copy EFI**
   - Mount the EFI partition of your USB drive
   - Copy the `EFI` folder from this repository to the root of the EFI partition

3. **Configure BIOS/UEFI**
   - Apply the settings listed above in BIOS/UEFI Settings section

4. **Boot and Install**
   - Boot from the USB drive
   - Follow the macOS installation process
   - After installation, copy EFI to your internal drive's EFI partition

## 🛠️ Post-Installation

### Essential Steps
1. **Generate new SMBIOS**
   - Use [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS)
   - Update `config.plist` with unique serial numbers

2. **Install WiFi Solution** (Optional)
   - Consider USB WiFi adapters with macOS-compatible chipsets
   - Recommended: TP-Link AC600 or similar Realtek-based adapters

3. **Update Kexts**
   - Keep kexts updated for better compatibility

### Recommended Tools
- [Hackintool](https://github.com/headkaze/Hackintool) - System information and patching
- [SSDTTime](https://github.com/corpnewt/SSDTTime) - SSDT generation
- [MountEFI](https://github.com/corpnewt/MountEFI) - Easy EFI partition mounting
- [MonitorControl](https://github.com/MonitorControl/MonitorControl) - External monitor brightness control

## 🔄 Updates

| Date | Version | Changes |
|------|---------|---------|
| Aug 16, 2025 | 1.0.0 | Initial release for Dell Latitude E5440 |

## 🐛 Known Issues

- **No Brightness Control**: Internal display brightness cannot be adjusted via keyboard or system preferences
- **No WiFi/Bluetooth**: Intel wireless cards are not compatible. Use USB adapters or replace with compatible cards
- **Limited Graphics**: Basic Intel HD 4400 functionality, may not support all graphics-intensive applications
- **BD PROCHOT**: Resolved using .efi driver at boot time

### Workarounds
- **WiFi**: Use USB WiFi adapter or ethernet connection
- **Brightness**: Use external monitor controls or third-party software
- **Bluetooth**: Use USB Bluetooth adapter if needed

## 📞 Support

If you encounter issues:
1. Check the [known issues](#-known-issues) section
2. Review [Dortania's guides](https://dortania.github.io/)
3. Ask for help in [r/hackintosh](https://www.reddit.com/r/hackintosh/)
4. Check similar configurations: [axemre/OpenCore-Dell-Latitude-E5440](https://github.com/axemre/OpenCore-Dell-Latitude-E5440)
5. Open an issue in this repository

## 🙏 Credits

- [OpenCore Team](https://github.com/acidanthera/OpenCorePkg) for the amazing bootloader
- [Dortania](https://dortania.github.io/) for comprehensive OpenCore guides
- [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS) for SMBIOS generation tool
- [ProperTree](https://github.com/corpnewt/ProperTree) for plist editing
- [axemre/OpenCore-Dell-Latitude-E5440](https://github.com/axemre/OpenCore-Dell-Latitude-E5440) for valuable configuration insights
- The Hackintosh community for continuous support and knowledge sharing

## ⚠️ Disclaimer

This EFI configuration is provided as-is for educational purposes. Use at your own risk. Always backup your data before attempting to install macOS on non-Apple hardware. Not fully tested - verify all functionality before using as your main system.
