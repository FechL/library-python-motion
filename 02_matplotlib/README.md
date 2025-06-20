# `matplotlib` untuk Visualisasi Gerakan dan Plotting Data

## 📌 Apa itu `matplotlib`?
`matplotlib` adalah library visualisasi paling populer di Python. Library ini memungkinkan kamu untuk:

- Menampilkan data posisi dan kecepatan dalam bentuk grafik
- Membuat animasi sederhana gerakan
- Menganalisis pola gerakan robotik dengan visual interaktif

## Contoh Dasar: Menampilkan Lintasan Gerakan

```python
import matplotlib.pyplot as plt
import numpy as np

# Data simulasi: lintasan sinusoidal
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.plot(x, y)
plt.title("Lintasan Gerakan Sumbu Y terhadap X")
plt.xlabel("Waktu (s)")
plt.ylabel("Posisi Y")
plt.grid(True)
plt.show()
```

## Contoh Tambahan: Visualisasi Dua Dimensi Gerakan Robot

```python
# Simulasi lintasan 2D
t = np.linspace(0, 2*np.pi, 100)
x = np.cos(t)
y = np.sin(t)

plt.plot(x, y, marker='o')
plt.title("Lintasan Gerakan Melingkar")
plt.xlabel("Posisi X")
plt.ylabel("Posisi Y")
plt.axis("equal")
plt.grid(True)
plt.show()
```

## Bonus: Visualisasi Animasi Sederhana Gerakan

```python
import matplotlib.pyplot as plt
import matplotlib.animation as animation
import numpy as np

fig, ax = plt.subplots()
xdata, ydata = [], []
ln, = plt.plot([], [], 'ro', animated=True)

def init():
    ax.set_xlim(0, 2*np.pi)
    ax.set_ylim(-1, 1)
    return ln,

def update(frame):
    xdata.append(frame)
    ydata.append(np.sin(frame))
    ln.set_data(xdata, ydata)
    return ln,

ani = animation.FuncAnimation(fig, update, frames=np.linspace(0, 2*np.pi, 100),
                              init_func=init, blit=True)
plt.title("Animasi Gerakan Sinusoidal")
plt.show()
```

📄 Dokumentasi Resmi: [https://matplotlib.org/stable/contents.html](https://matplotlib.org/stable/contents.html)


## 🔍 Kapan Digunakan dalam Programming Motion?

| Kebutuhan                          | Cocok?                                                   |
| ---------------------------------- | -------------------------------------------------------- |
| Visualisasi data posisi/kecepatan  | ✅                                                        |
| Evaluasi hasil filtering/algoritma | ✅                                                        |
| Simulasi lintasan dan trajektori   | ✅                                                        |
| Visualisasi gerakan waktu nyata    | ⚠️ (butuh integrasi dengan `FuncAnimation` atau `pygame`) |

| [◀️ Prev: 01 numpy dan scipy](/01_numpy_scipy/) | [🏠 Menu Utama](/) | [▶️ Next: 03 time dan theading](/03_time_threading/) |
| ---------------------------------------------- | ----------------- | --------------------------------------------------- |