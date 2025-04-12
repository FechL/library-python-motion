# 🎮 `pynput` atau `keyboard` untuk Simulasi Input Kendali

## 📌 Tujuan Penggunaan
Dalam sistem *programming motion*, input dari pengguna (misalnya tombol keyboard) bisa digunakan untuk:
- Mengendalikan arah gerakan
- Memberi perintah mulai/berhenti
- Meniru kontrol manual robot secara real-time

Python menyediakan dua library populer untuk ini: `pynput` dan `keyboard`.

## `pynput`

### Kelebihan:
- Tidak blocking (tidak menghambat eksekusi program lain)
- Bisa dijalankan di latar belakang

### Kekurangan:
- Lebih kompleks dari `keyboard`
- Tidak mendukung semua platform untuk simulasi penekanan tombol

### Contoh: Deteksi Tombol yang Ditekan

```python
from pynput.keyboard import Listener

def on_press(key):
    print(f"Tombol ditekan: {key}")

def on_release(key):
    if key == key.esc:
        return False  # berhenti jika Esc ditekan

# Jalankan listener
with Listener(on_press=on_press, on_release=on_release) as listener:
    listener.join()
```

📄 Dokumentasi Resmi:  
[https://pynput.readthedocs.io](https://pynput.readthedocs.io)

## `keyboard`

### Kelebihan:
- Lebih sederhana
- Deteksi tombol cepat dan langsung

### Kekurangan:
- Harus dijalankan dengan hak admin/root
- Tidak selalu kompatibel di Linux/MacOS

### Contoh: Kontrol Gerakan dengan Keyboard
```python
import keyboard

print("Tekan 'w', 's', 'a', 'd' untuk mengontrol. Tekan 'esc' untuk keluar.")
while True:
    if keyboard.is_pressed('w'):
        print("Maju")
    elif keyboard.is_pressed('s'):
        print("Mundur")
    elif keyboard.is_pressed('a'):
        print("Kiri")
    elif keyboard.is_pressed('d'):
        print("Kanan")
    elif keyboard.is_pressed('esc'):
        print("Keluar...")
        break
```

📄 Dokumentasi Resmi:  
[https://keyboard.readthedocs.io](https://keyboard.readthedocs.io)

## 🔍 Kapan Digunakan dalam Programming Motion?

| Fitur                                | `pynput` | `keyboard` |
| ------------------------------------ | -------- | ---------- |
| Deteksi penekanan tombol             | ✅        | ✅          |
| Non-blocking                         | ✅        | ❌          |
| Mudah digunakan                      | ❌        | ✅          |
| Diperlukan akses admin/root          | ❌        | ✅          |
| Multi-platform (Windows/Linux/macOS) | ⚠️        | ⚠️          |

Gunakan `keyboard` untuk prototipe cepat, dan `pynput` untuk aplikasi yang lebih kompleks atau interaktif.

| [◀️ Prev: 03 time dan threading](/03_time_threading/) | [🏠 Menu Utama](/) | [▶️ Next: 05 serial](/05_serial/) |
| ---------------------------------------------------- | ----------------- | -------------------------------- |