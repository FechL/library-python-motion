#  `time` dan `threading` untuk Simulasi Waktu Nyata

## 📌 `time`
Library built-in Python untuk:
- Mengatur delay antar gerakan
- Mengukur durasi eksekusi
- Sinkronisasi waktu dalam simulasi atau kontrol robot

### Contoh Penggunaan `time`
```python
import time

for i in range(5):
    print(f"Gerakan ke-{i}")
    time.sleep(1)  # delay 1 detik antar gerakan
```

### Pengukuran Durasi Eksekusi
```python
start = time.time()

# Proses simulasi
for i in range(1000000):
    _ = i**2

end = time.time()
print(f"Durasi eksekusi: {end - start:.4f} detik")
```

📄 Dokumentasi Resmi `time`:  
[https://docs.python.org/3/library/time.html](https://docs.python.org/3/library/time.html)

## 📌 `threading`
`threading` memungkinkan eksekusi **multitasking secara paralel**. Dalam konteks *programming motion*, ini berguna untuk:

- Menjalankan visualisasi sambil menerima input kendali
- Logging data sensor tanpa menghambat gerakan
- Mengontrol lebih dari satu motor/aktuator secara serempak

### Contoh Penggunaan `threading` untuk Gerakan Paralel
```python
import threading
import time

def gerakan_motor():
    for i in range(5):
        print("Motor bergerak...")
        time.sleep(1)

def logging_data():
    for i in range(5):
        print("Logging data sensor...")
        time.sleep(0.5)

# Jalankan keduanya secara paralel
t1 = threading.Thread(target=gerakan_motor)
t2 = threading.Thread(target=logging_data)

t1.start()
t2.start()

t1.join()
t2.join()
```

📄 Dokumentasi Resmi `threading`:  
[https://docs.python.org/3/library/threading.html](https://docs.python.org/3/library/threading.html)

## 🔍 Kapan Digunakan dalam Programming Motion?

| Fungsi                                | `time` | `threading` |
| ------------------------------------- | ------ | ----------- |
| Delay antar aksi gerakan              | ✅      |             |
| Pengukuran waktu                      | ✅      |             |
| Menjalankan dua fungsi bersamaan      |        | ✅           |
| Logging sensor saat motor bergerak    |        | ✅           |
| Menghindari eksekusi blocking tunggal |        | ✅           |

| [◀️ Prev: 02 matplotlib](/02_matplotlib/) | [🏠 Menu Utama](/) | [▶️ Next: 04 pynput dan keyboard](/04_pynput_keyboard/) |
| ---------------------------------------- | ----------------- | ------------------------------------------------------ |