*** Arken Windows Device Fingerprint Utility

A lightweight, offline Windows utility that generates a unique device fingerprint
using system-level identifiers. Built for IT teams, developers, and support
professionals who need a reliable way to identify and register Windows devices.

---

### 🌐 Live Project Page

 **View the full project page with screenshots, downloads, and details:**  
🔗 https://arkenapps.github.io/ArkenDeviceFingerprint/

> The project page includes:
> - Clean UI overview
> - Screenshot of the tool
> - Direct download for **Windows x64** and **Windows ARM64**
> - GitHub and company links

---

###  Key Features

- Works on **Windows x64 and ARM64**
- Fully **offline** (no internet required)
- No installation or dependencies
- Generates a **stable SHA-256–based Device ID**
- Displays system manufacturer, model, and device type
- Saves results automatically to the **Desktop**
- Console-based and copy-friendly
- Fast, secure, and transparent

---

### What Information Does It Collect?

The utility reads the following system identifiers:

- **BIOS Serial Number**
- **System UUID**
- **Windows Machine GUID**
- **System Manufacturer** (e.g., Dell, HP, Lenovo)
- **System Model** (e.g., Latitude, ThinkPad, Surface)
- **Device Type** (Laptop, Desktop, Virtual Machine)

These values are combined and hashed to produce a single **Device ID**.

> 🔒 No personal data is collected  
> 🌐 No information is transmitted outside the device

---

## 🔑 Device ID Explained

The **Device ID** is a SHA-256 hash generated from multiple system identifiers.
This provides:

- High uniqueness
- Reasonable stability across OS usage
- Resistance to casual spoofing
- Safe sharing (raw identifiers are not exposed)

Suitable for:
- Device registration
- Offline licensing
- Internal asset identification
- Support diagnostics

---

## 📂 Output

When executed, the tool:

1. Displays system details in the console
2. Saves a text file to the user’s Desktop:

```text
device_fingerprint.txt
