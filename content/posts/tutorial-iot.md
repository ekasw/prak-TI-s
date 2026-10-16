+++
date = '2026-10-12T22:56:01+08:00'
draft = false
title= 'Cara Install MicroPython Pada ESP32 dan ESP8266'

[cover]
    image = "/images/header1.jpg"
    alt = "Skema ESP32"
    caption = "Proyek IoT Menggunakan ESP"
+++
Kali ini kita akan coba cara mem-flash firmware MicroPython ke papan ESP32/ESP8266 menggunakan perangkat lunak IDE [uPyCraft](https://github.com/DFRobot/uPyCraft). Tools ini dapat berjalan di Windows, Linux, dan Mac OS X.

Sebelum melanjutkan tutorial ini, pastikan kita sudah menginstal uPyCraft IDE di komputer/laptop kesayangan… Jika belum dapat didownload dan diinstall secara gratis di sini: [GitHub — DFRobot/uPyCraft](https://github.com/DFRobot/uPyCraft). Dengan uPyCraft IDE yang diinstal di komputer, kita dapat dengan mudah mem-flash mikrokontroler ESP32 atau ESP8266 dengan firmware MicroPython.

Catatan: Setelah menginstal firmware MicroPython pada ESP32 atau ESP8266, kita dapat kembali dan menggunakan Arduino IDE lagi. Yang dilakukan hanya perlu mengunggah kode menggunakan Arduino IDE. Kemudian, jika ingin menggunakan MicroPython lagi, kita perlu mem-flash firmware MicroPython kembali.

Bagian 1 — Mengunduh dan Mem-flash Firmware MicroPython di ESP32
Untuk mengunduh firmware MicroPython versi terbaru untuk ESP32, buka halaman [Unduhan MicroPython berikut ini](http://micropython.org/download#esp32) dan gulir ke bawah ke bagian ESP32.

Anda akan melihat halaman web serupa (lihat gambar di bawah) dengan tautan terbaru untuk mengunduh file .bin ESP32 — misalnya: esp32–20181007-v1.9.4–631-g338635ccc.bin.
![gambar1](/images/20261016081903.png)
![](/images/Pasted%20image%2020261016172200.png)
Catatan: jika Anda menggunakan mikrokontroler yang berbeda (seperti PyBoard, WiPy, atau lainnya), buka halaman Unduhan MicroPython dan unduh firmware yang tepat untuk papan Anda.

Memilih Port Serial
Buka Alat > Serial dan pilih port COM ESP32 Anda (dalam kasus kami adalah COM5).
![gambar2](/images/Pasted%20image%2020261016081935.png)

**Peringatan**: Jika telah menghubungkan ESP32 ke komputer, tetapi tidak dapat menemukan Port ESP32 yang tersedia di IDE uPyCraft, ada beberapa kemungkinan: 1. Driver USB bermasalah atau belum diinstall, atau 2. Kabel USB yang dipakai adalah kabel tanpa kabel data (hanya untuk cas saja).

1. Jika tidak melihat port COM ESP yang tersedia, ini sering kali berarti kita belum menginstal driver USB. Perhatikan lebih cermat chip di sebelah regulator tegangan pada papan dan periksa namanya. Pada percobaan ini, kami mendapatkan informasi board yang digunakan adalah ESP32 DEVKIT V1 DOIT board menggunakan chip CP2102.
![gambar3](/images/Pasted%20image%2020261016081947.png)

Buka Google dan cari chip spesifik Anda untuk menemukan driver dan menginstalnya di sistem operasi Anda.

![[Pasted image 20261016070017.png]]

Anda dapat mengunduh driver CP2102 di situs web [Silicon Labs.](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers)

![[Pasted image 20261016070103.png]]

Setelah diinstal, restart IDE uPyCraft dan kita akan melihat port COM di menu Tools.

2. Jika telah menginstal driver, tetapi tidak dapat melihat perangkat, periksa kembali apakah sudah dipastikan menggunakan kabel USB dengan kabel data.

Kabel USB dari powerbank seringkali tidak memiliki kabel data (hanya diisi daya). Jadi, komputer tidak akan pernah menjalin komunikasi serial dengan ESP32. Menggunakan kabel USB yang tepat akan menyelesaikan masalahnya.

Memilih Board
Pilih Tools > Board. Pada tutorial ini kami menggunakan ESP32, so make sure you select the “esp32” option:
![[Pasted image 20261016070201.png]]

**Flashing/Uploading MicroPython Firmware**
Langkah terakhir, go to Tools > BurnFirmware menu to flash your ESP32 with MicroPython.
![[Pasted image 20261016070345.png]]

Select all these options to flash the ESP32 board:

board: esp32
burn_addr: 0x1000
erase_flash: yes
com: COMX (in our case it’s COM5)
Firmware: Select “Users” and choose the ESP32 .bin file downloaded earlier
![[Pasted image 20261016070407.png]]
Setelah menekan tombol “Pilih”, navigasikan ke folder Unduhan Anda dan pilih file .bin ESP32:
![[Pasted image 20261016070419.png]]

Setelah semua pengaturan dipilih, tahan tombol “BOOT/FLASH” di papan ESP32 Anda:
![[Pasted image 20261016070438.png]]

Sambil menahan “BOOT/FLASH”, klik tombol “ok” di jendela update firmware:
![[Pasted image 20261016070449.png]]

Saat proses “EraseFlash” dimulai, Anda dapat melepaskan tombol “BOOT/FLASH”. Setelah beberapa detik, firmware akan di-flash ke papan ESP32 Anda.
![[Pasted image 20261016070530.png]]

Catatan: jika bilah “EraseFlash” tidak bergerak dan Anda melihat pesan kesalahan yang mengatakan “erase false.”, itu berarti ESP32 Anda tidak dalam mode berkedip. Anda perlu mengulangi semua langkah yang dijelaskan sebelumnya dan menahan tombol “BOOT/FLASH” lagi untuk memastikan ESP32 Anda masuk ke mode berkedip.
![[Pasted image 20261016070604.png]]

**Bagian 2 — Mengunduh dan Mem-flash Firmware MicroPython di ESP8266**
Untuk mengunduh firmware MicroPython versi terbaru untuk ESP8266, buka halaman [Unduhan MicroPython berikut ini](http://micropython.org/download#esp8266) dan gulir ke bawah ke bagian ESP8266.
Anda akan melihat halaman web serupa (lihat gambar di bawah) dengan tautan terbaru untuk mengunduh file .bin ESP8266 — misalnya: esp8266–20180511-v1.9.4.bin.
![[Pasted image 20261016070816.png]]
Catatan: jika Anda menggunakan papan yang berbeda (seperti PyBoard, WiPy, atau lainnya), buka halaman [Unduhan MicroPython berikut ini ](http://micropython.org/downloads)dan unduh firmware yang tepat untuk papan Anda.

**Memilih Port Serial**
Buka Alat > Serial dan pilih port COM ESP8266 Anda (dalam kasus kami adalah COM5).
![[Pasted image 20261016070920.png]]

Penting: jika Anda mencolokkan papan ESP32 ke komputer, tetapi Anda tidak dapat menemukan Port ESP32 yang tersedia di IDE uPyCraft, itu mungkin salah satu dari dua masalah ini: 1. Driver USB hilang atau 2. Kabel USB tanpa kabel data.

1. Jika Anda tidak melihat port COM ESP Anda tersedia, ini sering kali berarti Anda tidak menginstal driver USB. Perhatikan lebih dekat chip di sebelah pengatur tegangan di atas kapal dan periksa namanya. Pada tutorial ini kebetulan kami mendapatkan informasi board ESP-12E NodeMCU ESP8266 menggunakan chip CP2102.
![[Pasted image 20261016071021.png]]

Buka Google dan cari chip spesifik Anda untuk menemukan driver dan menginstalnya di sistem operasi Anda.
![[Pasted image 20261016071037.png]]
Anda dapat mengunduh driver CP2102 di situs web [Silicon Labs berikut ini](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers).
![[Pasted image 20261016071117.png]]

Setelah diinstal, mulai ulang IDE uPyCraft dan Anda akan melihat port COM di menu Alat.

2. Jika Anda telah menginstal driver, tetapi Anda tidak dapat melihat perangkat, periksa kembali apakah Anda menggunakan kabel USB dengan kabel data.

Kabel USB dari powerbank seringkali tidak memiliki kabel data (hanya diisi daya). Jadi, komputer Anda tidak akan pernah menjalin komunikasi serial dengan ESP8266 Anda. Menggunakan kabel USB yang tepat akan menyelesaikan masalah Anda.

**Memilih Papan**
Buka Alat > Board. Untuk tutorial ini, kami berasumsi bahwa Anda menggunakan ESP8266, jadi pastikan Anda memilih opsi “esp8266”:
![[Pasted image 20261016071136.png]]

**Mem-flash/Mengunggah Firmware MicroPython**
Terakhir, buka menu Tools > BurnFirmware untuk mem-flash ESP32 Anda dengan MicroPython.
![[Pasted image 20261016071157.png]]

Pilih semua opsi ini untuk mem-flash papan ESP8266:

Papan: ESP8266
burn_addr: 0x0
erase_flash: Iya
com: COMX (dalam kasus kami COM5)
Firmware: Pilih “Pengguna” dan pilih file .bin ESP8266 yang diunduh sebelumnya
![[Pasted image 20261016071212.png]]
Setelah menekan tombol “Pilih”, navigasikan ke folder Unduhan Anda dan pilih file .bin ESP8266:
![[Pasted image 20261016071225.png]]

Setelah semua pengaturan dipilih, tahan tombol “BOOT/FLASH” di papan ESP8266 Anda:
![[Pasted image 20261016071238.png]]

Sambil menahan “BOOT/FLASH”, klik tombol “ok” di jendela update firmware:
![[Pasted image 20261016071255.png]]

Saat proses “EraseFlash” dimulai, Anda dapat melepaskan tombol “BOOT/FLASH”. Setelah beberapa detik, firmware akan di-flash ke papan ESP8266 Anda.
![[Pasted image 20261016071311.png]]

Catatan: jika tanda pada “EraseFlash” tidak bergerak dan Anda melihat pesan kesalahan yang bertuliskan “erase false.”, itu berarti ESP8266 Anda tidak dalam flashing mode. Anda perlu mengulangi semua langkah yang dijelaskan sebelumnya dan menahan tombol “BOOT/FLASH” lagi untuk memastikan ESP8266 Anda masuk ke flashing mode.
![[Pasted image 20261016071319.png]]

Kesimpulan
Semoga tutorial ini bermanfaat bagi pengembang IoT yang ingin menggunakan skrip bahasa pemrograman berbasis Python. ESP32/ESP8266 kita sekarang telah selesai di-flash dengan firmware MicroPython. Untuk mempelajari lebih lanjut tentang MicroPython, baca: [Memulai MicroPython di ESP32 dan ESP8266](https://randomnerdtutorials.com/getting-started-micropython-esp32-esp8266/).