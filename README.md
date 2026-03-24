# rem Plymouth Theme
![rem (1)](https://github.com/user-attachments/assets/2311ab46-1a99-409c-bd26-589b0f937c2c)


A guide to installing the `rem` Plymouth boot splash theme on Debian-based Linux systems (Ubuntu, Parrot OS, Kali, etc.).

## Prerequisites

- A Debian-based Linux distro
- `git` installed
- `sudo` privileges

## Installation

### 1. Clone the theme

```bash
git clone https://github.com/yourusername/yourrepo.git
```

### 2. Copy the theme folder

```bash
sudo cp -r rem /usr/share/plymouth/themes/rem
```

### 3. Set it as the default theme

```bash
sudo plymouth-set-default-theme rem
```

### 4. Rebuild the initramfs

```bash
sudo update-initramfs -u
```

Reboot to see the theme applied.

---

## Verify it's set

```bash
cat /etc/plymouth/plymouthd.conf
```

You should see:

```ini
[Daemon]
Theme=rem
```

---

## Switching back

To revert to your distro's original theme, replace `rem` with the original theme name (e.g. `parrot6`, `bgrt`, `spinner`):

```bash
sudo plymouth-set-default-theme parrot6
sudo update-initramfs -u
```

---

## Preview without rebooting

```bash
sudo plymouthd --no-daemon &
sudo plymouth --show-splash
sleep 5
sudo plymouth quit
```

> **Note:** The preview may look slightly off depending on your display server. It will render correctly at boot.
