# Mi USB Driver

USB drivers for **Xiaomi / Mi / Redmi / POCO** devices on Windows. Install these so your
computer can recognize your phone for **ADB**, **Fastboot**, **MTP file transfer**, and
flashing / unlocking operations with tools like Mi Flash and Mi Unlock.

> **Download:** the drivers are published on the
> [**Releases**](../../releases/latest) page as **`Driver.zip`**.
> Extracted from the Mi Unlock Tool `7.6.727.43`.

---

## Why you need this

Out of the box, Windows often fails to properly detect a Xiaomi device in ADB or Fastboot
mode, showing it as an **unknown device** in Device Manager. These drivers register the
correct USB interfaces so tools such as `adb`, `fastboot`, Mi Flash Tool, and Mi Unlock
Tool can communicate with the phone.

Typical use cases:

- Transferring files between phone and PC
- Running `adb` / `fastboot` commands
- Unlocking the bootloader (Mi Unlock)
- Flashing ROMs / firmware (Mi Flash)
- Recovery and debugging

---

## Requirements

- Windows 10 or 11 (32-bit or 64-bit)
- A USB data cable (not charge-only)
- **USB debugging** enabled on the phone (for ADB)

---

## Enabling USB debugging on the phone

1. Go to **Settings → About phone**.
2. Tap **MIUI version** (or **OS version**) seven times to unlock **Developer options**.
3. Go to **Settings → Additional settings → Developer options**.
4. Enable **USB debugging**.
5. Connect the phone and tap **Allow** on the "Allow USB debugging?" prompt.

---

## Installation

1. Download **`Driver.zip`** from the [Releases](../../releases/latest) page.
2. Right-click the downloaded file → **Extract All…** to unzip it to a folder.
3. Connect your Xiaomi device with a USB cable.
4. Install via **Device Manager** (steps below).

### Install via Device Manager

1. Open **Device Manager** (`Win + X → Device Manager`).
2. Find the unknown / Xiaomi device (often under *Other devices* or *Portable Devices*,
   possibly with a yellow warning icon).
3. Right-click it → **Update driver**.
4. Choose **Browse my computer for drivers**.
5. Point it to the folder where you extracted `Driver.zip` (keep **Include subfolders**
   checked) and click **Next** to finish the wizard.
6. Reboot your PC if prompted.

> If Windows blocks the unsigned driver, temporarily disable **driver signature
> enforcement** (see [Troubleshooting](#troubleshooting)) and repeat the steps.

---

## Verifying the installation

With **ADB platform-tools** installed, open a terminal and run:

```bash
adb devices
```

You should see your device's serial number listed. In Fastboot mode:

```bash
fastboot devices
```

If a device is listed, the driver is working.

---

## Troubleshooting

| Problem | Fix |
| --- | --- |
| Device not detected | Try a different USB cable/port; use a rear USB 2.0 port on desktops. |
| Shows as "unknown device" | Do a **manual install** via Device Manager (see above). |
| Driver blocked on install | Disable **driver signature enforcement** temporarily, then install. |
| `adb` sees nothing | Re-check **USB debugging** is on and accept the RSA prompt on the phone. |
| Fastboot not recognized | Reboot phone to Fastboot (`Power + Volume Down`) and reinstall the driver. |

---

## Disclaimer

These drivers are provided **as-is** for convenience. Flashing, unlocking, or modifying
your device can void the warranty and may brick the device if done incorrectly. Use at
your own risk. Xiaomi, Mi, Redmi, and POCO are trademarks of Xiaomi Inc.; this repository
is not affiliated with or endorsed by Xiaomi.

---

## License

See the [LICENSE](LICENSE) file if present, otherwise these drivers are redistributed for
personal, non-commercial use.
