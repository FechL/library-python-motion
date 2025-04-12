# `numpy` dan `scipy` untuk Komputasi Numerik dan Filtering

## 📌 Apa itu `numpy`?
`numpy` adalah library fundamental untuk komputasi numerik dalam Python. Library ini menyediakan array multidimensi yang efisien dan operasi matematis cepat, cocok untuk manipulasi data posisi, kecepatan, akselerasi, dan lainnya.

### Contoh Penggunaan `numpy`
```python
import numpy as np

# Membuat array posisi dari gerakan linear
x = np.linspace(0, 10, 100)  # 100 titik dari 0 sampai 10
v = np.gradient(x)           # estimasi kecepatan (turunan pertama)
```

📄 Dokumentasi Resmi: [https://numpy.org/doc/](https://numpy.org/doc/)

## 📌 Apa itu `scipy`?
`scipy` adalah library yang memperluas fungsionalitas `numpy` dengan menyediakan berbagai algoritma ilmiah, termasuk filtering sinyal, interpolasi, optimasi, dan lainnya.

### Contoh Penggunaan: Filter Low-pass pada Data Posisi
```python
from scipy.signal import butter, filtfilt
import numpy as np
import matplotlib.pyplot as plt

# Data simulasi (dengan noise)
t = np.linspace(0, 1, 100)
pos = np.sin(2 * np.pi * 5 * t) + np.random.normal(0, 0.5, 100)

# Fungsi filter low-pass
def lowpass_filter(data, cutoff=2.5, fs=100, order=4):
    nyq = 0.5 * fs
    normal_cutoff = cutoff / nyq
    b, a = butter(order, normal_cutoff, btype='low', analog=False)
    y = filtfilt(b, a, data)
    return y

filtered_pos = lowpass_filter(pos)

# Visualisasi hasil filtering
plt.plot(t, pos, label='Asli + noise')
plt.plot(t, filtered_pos, label='Setelah filter', linewidth=2)
plt.legend()
plt.title("Filtering Data Gerakan")
plt.xlabel("Waktu (s)")
plt.ylabel("Posisi")
plt.grid(True)
plt.show()
```

📄 Dokumentasi Resmi: [https://docs.scipy.org/doc/scipy/](https://docs.scipy.org/doc/scipy/)

## 🔍 Kapan Digunakan dalam Programming Motion?

| Fungsi                       | `numpy` | `scipy`          |
| ---------------------------- | ------- | ---------------- |
| Array posisi dan kecepatan   | ✅       |                  |
| Perhitungan turunan/integral | ✅       | ✅                |
| Filtering sinyal sensor      |         | ✅ (filter, FFT)  |
| Interpolasi data gerakan     |         | ✅ (interp1d dll) |

 | [🏠 Menu Utama](/) | [▶️ Next: 01 matplotlib](/02_matplotlib/) |
 | ----------------- | ---------------------------------------- |