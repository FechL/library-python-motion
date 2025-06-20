# `serial` (PySerial) untuk Komunikasi dengan Perangkat seperti Arduino

## 📌 Apa itu `pyserial`?
`pyserial` adalah library Python untuk komunikasi **serial (UART)**. Umumnya digunakan untuk:
- Berkomunikasi dengan **Arduino**, STM32, ESP32, dan mikrokontroler lainnya
- Mengirim atau menerima data sensor dan kendali
- Membangun jembatan antara program Python dan hardware robot

## Contoh Dasar: Kirim Data ke Arduino
```python
import serial
import time

# Sesuaikan port dengan COM Arduino kamu
ser = serial.Serial('COM4', 9600, timeout=1)  
time.sleep(2)  # Tunggu koneksi

while True:
    command = input("Ketik '1' untuk menyalakan LED, '0' untuk mematikan: ")
    ser.write(command.encode())  # Kirim data
```

### Contoh di Sisi Arduino (untuk menerima data)
```cpp
void setup() {
  Serial.begin(9600);
  pinMode(13, OUTPUT);
}

void loop() {
  if (Serial.available()) {
    char data = Serial.read();
    if (data == '1') digitalWrite(13, HIGH);
    else if (data == '0') digitalWrite(13, LOW);
  }
}
```

## Menerima Data dari Arduino
```python
import serial
import time

ser = serial.Serial('COM4', 9600)
time.sleep(2)

while True:
    if ser.in_waiting > 0:
        data = ser.readline().decode().strip()
        print(f"Data dari Arduino: {data}")
```

📄 Dokumentasi Resmi:
[https://pyserial.readthedocs.io/en/latest/](https://pyserial.readthedocs.io/en/latest/)

## 🔍 Kapan Digunakan dalam Programming Motion?

| Kebutuhan                                   | Cocok?                  |
| ------------------------------------------- | ----------------------- |
| Mengirim perintah kontrol ke mikrokontroler | ✅                       |
| Membaca data sensor dari perangkat          | ✅                       |
| Menyinkronkan gerakan dengan sensor         | ✅                       |
| Komunikasi nirkabel (HC-05/ESP32 UART)      | ✅                       |
| Real-time streaming data posisi             | ⚠️ (tergantung baudrate) |

| [◀️ Prev: 04 pynput dan keyboard](/04_pynput_keyboard/) | [🏠 Menu Utama](/) | [▶️ Next: 06 other libraries](/06_other_libraries) |
| ------------------------------------------------------ | ----------------- | ------------------------------------------------- |