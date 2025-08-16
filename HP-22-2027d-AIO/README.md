# HP 22-2027d All-in-One Desktop - Hackintosh EFI

This folder contains the OpenCore EFI configuration for the HP 22-2027d All-in-One Desktop PC.

## 🖥️ Hardware Specifications

| Component | Details |
|-----------|---------|
| **Model** | HP 22-2027d All-in-One Desktop |
| **CPU** | Intel Core i5-4460T (4C/4T, 1.9GHz base, 2.7GHz boost, Haswell, 22nm) |
| **GPU** | Intel HD Graphics 4600 (integrated) |
| **RAM** | 4GB/6GB DDR3-1600 (1x4GB or 1x6GB SO-DIMM, expandable to 16GB) |
| **Storage** | Samsung SSD 120GB (SATA III interface) |
| **Audio** | Realtek ALC283 HD Audio Codec |
| **Ethernet** | Realtek RTL8111/8168B/8411 Gigabit Ethernet Controller |
| **WiFi/BT** | Not supported (no wireless card installed/working) |

## 🍎 macOS Compatibility

| macOS Version | Status | Notes |
|---------------|--------|-------|
| macOS Monterey (12.x) | ✅ Supported | Latest compatible version for Haswell architecture |
| macOS Big Sur (11.x) | ✅ Supported | Full compatibility with proper patches |
| macOS Catalina (10.15.x) | ✅ Supported | Native support, recommended for stability |
| macOS Mojave (10.14.x) | ✅ Supported | Excellent compatibility |

> **Note**: macOS Ventura (13.x) and newer versions have dropped support for Haswell processors (4th gen Intel). macOS Monterey is the latest officially supported version.

## 🔧 OpenCore Information

- **OpenCore Version**: 1.0.1 (Latest stable release as of August 2025)
- **SMBIOS**: iMac16,1 (Late 2015 iMac 21.5" - optimal for Haswell processors)
- **Configuration Date**: August 16, 2025
- **Target macOS**: macOS Monterey 12.7.x
- **Architecture**: x64 (64-bit)

## ✅ What's Working

- [x] Boot into macOS Monterey
- [ ] Graphics acceleration (Intel HD 4600 - currently showing 7MB VRAM issue)
- [x] Audio (speakers/headphones via Realtek ALC283)
- [x] Ethernet (Realtek RTL8111/8168B gigabit connection)
- [x] USB 2.0 and USB 3.0 ports
- [ ] Sleep/Wake functionality - *Not tested yet*
- [x] Webcam (integrated HD webcam)
- [x] Microphone (built-in microphone array)
- [ ] Power management (SpeedStep, C-states) - *Not tested yet*
- [ ] Hardware acceleration for video playback - *Not tested yet*
- [ ] App Store and iCloud services - *Not tested yet*
- [ ] Software updates - *Not tested yet*

## ❌ What's Not Working

- [x] Graphics acceleration (Intel HD 4600 shows only 7MB VRAM instead of full acceleration)
- [x] WiFi/Bluetooth (no wireless card installed or supported)
- [x] AirDrop/Handoff (due to lack of compatible WiFi/BT)
- [x] macOS Ventura and newer (Haswell limitation)

## 🔧 Current Status

**Testing Phase**: This EFI configuration is currently in early testing. While the system boots successfully into macOS Monterey, most hardware features require further testing and configuration.

**Graphics Issue**: The main priority is resolving the Intel HD 4600 graphics acceleration. Currently experiencing the common "7MB VRAM" issue which indicates graphics acceleration is not properly enabled.

## ⚙️ BIOS/UEFI Settings

### Enable:
- [x] UEFI Boot Mode
- [x] AHCI for SATA drives
- [x] Above 4G Decoding (if available in HP BIOS)
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

> **HP BIOS Note**: Some settings may not be available in HP's limited BIOS interface. Focus on the essential ones: UEFI mode, AHCI, and disabling Secure Boot.

## 📦 Installation Instructions

### Prerequisites
1. USB drive (8GB or larger)
2. macOS installer
3. [OpenCore Configurator](https://mackie100projects.altervista.org/opencore-configurator/) or [ProperTree](https://github.com/corpnewt/ProperTree)

### Steps
1. **Prepare USB Installer**
   ```bash
   # Use createinstallmedia or tools like gibMacOS
   sudo /Applications/Install\ macOS\ [Version].app/Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
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

2. **Enable FileVault** (Optional)
   - Can be enabled after confirming system stability

3. **Update Kexts**
   - Keep kexts updated for better compatibility

### Recommended Tools
- [Hackintool](https://github.com/headkaze/Hackintool) - System information and patching
- [SSDTTime](https://github.com/corpnewt/SSDTTime) - SSDT generation
- [MountEFI](https://github.com/corpnewt/MountEFI) - Easy EFI partition mounting

## 🔄 Updates

| Date | Version | Changes |
|------|---------|---------|
| Aug 16, 2025 | 1.0.0 | Initial release for HP 22-2027d with OpenCore 1.0.1 |

## 🐛 Known Issues

- **No WiFi/Bluetooth**: The system lacks a compatible wireless card. Consider using USB WiFi adapters with macOS-compatible chipsets (e.g., Realtek RTL8192CU)
- **Limited RAM**: 4GB/6GB may be insufficient for modern macOS usage. Upgrade to 8GB or 16GB DDR3 SO-DIMM for better performance
- **macOS Version Limitation**: Haswell processors are limited to macOS Monterey (12.x) as the maximum supported version

## 📞 Support

If you encounter issues:
1. Check the [known issues](#-known-issues) section
2. Review [Dortania's guides](https://dortania.github.io/)
3. Ask for help in [r/hackintosh](https://www.reddit.com/r/hackintosh/)
4. Open an issue in this repository

## 🙏 Credits

- [OpenCore Team](https://github.com/acidanthera/OpenCorePkg)
- [Dortania](https://dortania.github.io/) for excellent documentation
- The Hackintosh community

## ⚠️ Disclaimer

This EFI configuration is provided as-is. Use at your own risk. Always backup your data before attempting to install macOS on non-Apple hardware.
