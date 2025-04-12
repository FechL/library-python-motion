# 📚 Pengenalan Library Eksternal untuk Programming Motion

Dalam pengembangan sistem *Programming Motion*, Python memiliki banyak library eksternal yang mempermudah implementasi sistem gerakan, baik untuk simulasi maupun interaksi langsung dengan perangkat keras.

Berikut beberapa library penting yang akan digunakan:

## Library yang Digunakan dalam Programming Motion

| No  | Library                  | Fungsi                                                                                                                                                                                                      | Link Folder                  |
| --- | ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------- |
| 1   | `numpy` dan `scipy`      | Digunakan untuk komputasi numerik, manipulasi data sensor, dan perhitungan matematika. `scipy` cocok untuk filtering sinyal dan analisis frekuensi.                                                         | [klik](/01_numpy_scipy/)     |
| 2   | `matplotlib`             | Digunakan untuk visualisasi data gerakan dalam bentuk grafik. Cocok untuk memantau posisi, kecepatan, dan lintasan gerak.                                                                                   | [klik](/02_matplotlib/)      |
| 3   | `time` dan `threading`   | `time` digunakan untuk simulasi delay dan pengukuran waktu. `threading` memungkinkan eksekusi paralel, seperti menjalankan kontrol dan logging secara bersamaan.                                            | [klik](/03_time_threading/)  |
| 4   | `pynput` atau `keyboard` | Library untuk membaca input dari keyboard secara real-time, digunakan untuk kendali manual dalam simulasi robotik.                                                                                          | [klik](/04_pynput_keyboard/) |
| 5   | `serial`                 | Digunakan untuk komunikasi serial antara Python dan perangkat seperti Arduino. Berguna dalam sistem kendali atau umpan balik dari perangkat keras.                                                          | [klik](/05_serial/)          |
| 6   | `Other Libraries`        | Library tambahan seperti `opencv-python`, `pygame`, `smbus2`, `RPi.GPIO`, `asyncio`, `tkinter`, `loguru` untuk berbagai fungsi seperti pengolahan citra, kontrol grafis, komunikasi I2C, GPIO, dan logging. | [klik](/06_other_libraries/) |

## Cara Menambahkan Library di Python

Untuk menggunakan library eksternal dalam Python, kamu perlu mengimpor library tersebut terlebih dahulu. Berikut adalah cara umum untuk mengimpor library:

### 1. Menggunakan `import`
```python
import numpy
```
Cara ini mengimpor seluruh library dengan nama lengkapnya. Untuk menggunakan fungsi atau objek dari library, kamu harus menyebutkan nama library terlebih dahulu, seperti `numpy.array()`.

### 2. Menggunakan `from ... import`
```python
from numpy import array
```
Dengan cara ini, kamu mengimpor hanya fungsi atau objek tertentu dari library. Kamu bisa langsung menggunakan fungsi tersebut tanpa perlu menyebutkan nama library, seperti `array()`.

### 3. Menggunakan `import ... as`
```python
import numpy as np
```
Dengan cara ini, kamu mengimpor library dan memberinya alias, sehingga lebih mudah digunakan. Misalnya, kamu bisa menggunakan `np.array()` alih-alih `numpy.array()`.

Jika kamu belum menginstal library yang diperlukan, kamu bisa menginstalnya terlebih dahulu menggunakan `pip`:
```bash
pip install nama-library
```

## Kontribusi

Jika kamu ingin menambahkan atau memperbaiki informasi, fork repository ini dan kirimkan Pull Request. Terima kasih!