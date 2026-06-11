# hypra-dotfiles
Hypra Dotfiles — Glass-first Hyprland rice. Blur everything, frost the rest.
#  Hypra Dotfiles

**Konfigurasi Hyprland full glassmorphism untuk Arch Linux — jendela transparan, blur berlapis, palet Arctic Nord, dan Waybar yang melayang.**

Hypra adalah setup desktop yang menggabungkan estetika kaca beku dengan fungsionalitas Hyprland modern. Setiap elemen dirancang dengan blur multi-pass, opacity dinamis, dan animasi halus untuk menciptakan pengalaman visual yang premium.

---

## Fitur Utama

- **Blur 4-Pass** — Efek frosted glass berlapis pada setiap window
- **Opacity Dinamis** — Terminal 88%, VSCode 94%, Firefox 96% (tergantung app)
- **Border Animasi** — Gradient es biru berputar di window aktif
- **Waybar Melayang** — Status bar transparan dengan padding dari tepi layar
- **Animasi Smooth** — Slide + bounce saat pindah workspace
- **Hyprlock Glass** — Lock screen dengan blur screenshot real-time
- **Palet Arctic Nord** — Warna biru-putih yang konsisten di semua aplikasi
- **Wofi Launcher** — App launcher dengan efek glass yang responsif
- **Mako Notifications** — Notifikasi desktop transparan dan elegan

---

##  Persyaratan

- **OS**: Arch Linux (atau distro berbasis Arch)
- **DE**: Hyprland
- **Font**: JetBrains Mono (akan diinstall otomatis)
- **Kuota disk**: ~500MB untuk dependencies

##  Instalasi Cepat

```bash
# Clone atau extract zip
git clone https://github.com/yourusername/hypra-dotfiles.git
cd hypra-dotfiles

# Jalankan installer
chmod +x install.sh
./install.sh
```

**Atau manual:**

```bash
# Buat folder config
mkdir -p ~/.config/{hypr,waybar,wofi,mako,gtk-3.0}

# Copy file-file
cp -r hypr/* ~/.config/hypr/
cp -r waybar/* ~/.config/waybar/
cp -r wofi/* ~/.config/wofi/
cp -r mako/* ~/.config/mako/
cp -r gtk-3.0/* ~/.config/gtk-3.0/

# Jalankan sistem
Hyprland
```

---

##  Keybinding Penting

| Kombinasi | Fungsi |
|-----------|--------|
| `Super + Enter` | Buka Terminal (Kitty) |
| `Super + R` | Buka App Launcher (Wofi) |
| `Super + B` | Buka Browser (Firefox) |
| `Super + E` | File Manager (Thunar) |
| `Super + Q` | Tutup Window |
| `Super + F` | Fullscreen |
| `Super + V` | Toggle Floating |
| `Super + L` | Lock Screen |
| `Super + 1-10` | Pindah Workspace |
| `Super + Shift + 1-10` | Pindah Window ke Workspace |
| `Print` | Screenshot Area |
| `Shift + Print` | Screenshot & Simpan |
| `Super + ↑↓←→` | Focus Window |
| `Super + Shift + ↑↓←→` | Move Window |
| `Super + Ctrl + ↑↓←→` | Resize Window |

---

##  Struktur Folder

```
hypra-dotfiles/
├── hypr/
│   ├── hyprland.conf      # Config utama WM
│   ├── hyprlock.conf      # Lock screen
│   └── hyprpaper.conf     # Wallpaper daemon
├── waybar/
│   ├── config.jsonc       # Status bar config
│   └── style.css          # Glass styling
├── wofi/
│   ├── config             # App launcher config
│   └── style.css          # Launcher styling
├── mako/
│   └── config             # Notification config
├── gtk-3.0/
│   └── settings.ini       # GTK theme settings
├── install.sh             # Script installer otomatis
└── README.md              # Dokumentasi ini
```

---

##  Tema & Palet Warna

**Arctic Nord Palette:**
- **Frost** (Background): `#0f141e`
- **Ice Blue**: `#88c0d0`
- **Snow**: `#eceff4`
- **Accent Red**: `#bf616a`
- **Accent Yellow**: `#ebcb8b`
- **Accent Green**: `#a3be8c`

Semua elemen UI menggunakan palet ini dengan opacity layer untuk efek glass yang konsisten.

---

##  Rekomendasi Wallpaper

Untuk hasil visual terbaik, gunakan wallpaper dengan warna **gelap & kaya**:
- Deep blue (#1a2332)
- Dark purple (#2d1b3d)
- Charcoal black (#0d0d0d)
- Navy dengan accent warna

Wallpaper gelap membuat efek glass blur terlihat lebih dramatis dan premium. 

**Tempat:** Letakkan di `~/Pictures/wallpaper.jpg` atau ubah path di `~/.config/hypr/hyprpaper.conf`

---

##  Customisasi

### Mengubah Blur Strength
Edit `~/.config/hypr/hyprland.conf`:
```conf
blur {
    size   = 10      # 1-20 (lebih tinggi = lebih blur)
    passes = 4       # 1-5 passes
    noise  = 0.02    # 0.00-1.00
}
```

### Mengubah Opacity
```conf
general {
    active_opacity   = 0.88    # Window aktif
    inactive_opacity = 0.72    # Window tidak aktif
}
```

### Mengubah Animasi
```conf
animations {
    animation = windows, 1, 5, overshot, slide
    # Format: name, duration, delay, curve, direction
}
```

### Mengubah Tema Waybar
Edit `~/.config/waybar/style.css` untuk warna, spacing, dan styling.

---

##  Troubleshooting

### Blur tidak bekerja?
```bash
# Pastikan GPU driver sudah install dengan baik
glxinfo | grep "renderer"

# Hyprland perlu driver yang support EGL
# Update sistem Anda
sudo pacman -Syu
```

### Waybar tidak muncul?
```bash
# Restart Waybar
killall waybar
waybar &

# Atau reload Hyprland
Super + Shift + R
```

### Font tidak benar?
```bash
sudo pacman -S ttf-jetbrains-mono-nerd
fc-cache -fv
```

### Screenshot tidak jalan?
```bash
# Install dependencies
sudo pacman -S grim slurp wl-clipboard
```

---

##  Package yang Diinstall

**Core:**
- `hyprland` — Window manager
- `hyprpaper` — Wallpaper daemon
- `hyprlock` — Screen lock

**UI:**
- `waybar` — Status bar
- `wofi` — App launcher
- `mako` — Notification daemon

**Terminal & Apps:**
- `kitty` — Terminal emulator
- `firefox` — Web browser
- `thunar` — File manager

**Utilities:**
- `pipewire wireplumber` — Audio server
- `grim slurp` — Screenshot tools
- `brightnessctl` — Brightness control
- `network-manager-applet` — Network manager
- `polkit-gnome` — Authorization agent

**Fonts & Icons:**
- `ttf-jetbrains-mono-nerd` — Code font
- `papirus-icon-theme` — Icon theme
- `bibata-cursor-theme` — Cursor theme

---

##  Dark Mode Otomatis

Semua aplikasi sudah dikonfigurasi untuk dark mode:
- GTK3: `adw-gtk3-dark`
- Qt5: Dark theme auto-detect
- Terminal: Dark colorscheme

---

##  Kontribusi

Punya ide untuk meningkatkan Hypra? Pull request welcome! 

Fitur yang dinanti:
- [ ] Tema light glassmorphism
- [ ] Hyprland plugin support
- [ ] Custom widget untuk Waybar
- [ ] Preset wallpaper bundled

---

##  Lisensi

MIT License — Bebas digunakan, dimodifikasi, dan didistribusikan.

---

##  Support

Jika ada masalah atau pertanyaan:
1. Cek Troubleshooting section
2. Buka issue di GitHub
3. Konsultasi Hyprland wiki: https://wiki.hyprland.org

---

