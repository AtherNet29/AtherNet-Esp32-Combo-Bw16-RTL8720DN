<img width="186" height="28" alt="image" src="https://github.com/user-attachments/assets/6c9623e5-a78d-44c0-a29e-ef4bdda9eccc" />
<img width="193" height="28" alt="image" src="https://github.com/user-attachments/assets/44c926c8-ff3c-4d8f-8dc7-2aeafaddbb5c" />
<img width="158" height="28" alt="image" src="https://github.com/user-attachments/assets/31e5063f-5ba2-4e9d-b342-08fbf53b2c2a" />

<img width="252" height="20" alt="image" src="https://github.com/user-attachments/assets/1490839f-dd3a-4fdb-83cf-176b0278b3e6" />
⚡ AETHERNET PRO
Advanced Multi-Vector WiFi & Bluetooth Security Audit Tool
Satu modul untuk menguji ketahanan jaringan 2.4GHz, 5GHz, hingga Bluetooth.

🌟 Mengapa AETHERNET PRO Berbeda?
Sebagian besar tool hanya mengandalkan ESP32. AETHERNET PRO menggunakan arsitektur Distributed Attack System yang menggabungkan kekuatan 3 mikrokontroler berbeda secara bersamaan:

ESP32: Sebagai Otak Utama, Web Server, dan Penangkap Password.
BW16: Khusus menangani serangan Deauthentication yang lebih stabil ke jaringan 2.4GHz & 5GHz.
Dual NRF24L01: Menjalankan Continuous Wave Jamming untuk menguji frekuensi Bluetooth tanpa membebani CPU utama.
Hasilnya? Serangan berjalan mulus, UI tetap responsif, dan tingkat keberhasilan capture jauh lebih tinggi.

🎯 Fitur Unggulan
📡 Serangan WiFi (2.4GHz & 5GHz)
Smart Deauth Attack: Memutus koneksi target secara selektif menggunakan BW16, memaksa perangkat otomatis terhubung ke jaringan palsu (Evil Twin).
Evil Twin & Captive Portal: Kloning jaringan target 100% identik (Termasuk SSID & Channel). Mendukung Custom HTML untuk halaman phising yang sangat realistis.
Rogue AP: Membuat Access Point palsu mandiri dengan halaman login (Google/Facebook style) untuk menangkap kredensial.
Beacon Spam: Banjiri area dengan ratusan SSID palsu (Customizable hingga 50 nama berbeda).
Password Auto-Verify: Jika korban memasukkan password di halaman phising, ESP32 secara otomatis memverifikasi kebenaran password tersebut ke router asli secara real-time.
📻 Serangan Bluetooth
Dual Channel BT Jammer: Menggunakan 2x NRF24L01 (HSPI & VSPI) untuk melakukan Continuous Wave Jamming pada frekuensi BT, menguji kerentanan perangkat IoT Bluetooth.
🖥️ Interface & Kontrol
Dark Web Dashboard: Tampilan web futuristik, responsif di HP, dilengkapi sistem tema warna.
3D OLED Menu: Navigasi menggunakan 4 tombol fisik dengan tampilan menu bergaya 3D Scroll dan ikon khusus.
File Manager: Upload/Edit template HTML phising langsung dari browser.
BW16 Auto-Link: Otomatis mendeteksi dan menyinkronkan dengan modul BW16 via Serial.
🛠️ Spesifikasi Hardware yang Dibutuhkan
⚠️ PERHATIAN: Firmware ini dikodekan secara spesifik untuk pinout di bawah ini. Menggunakan pin lain akan menyebabkan kerusakan atau malfunction.

Komponen	Jumlah	Keterangan
ESP32 DevKit V1	1	Sebagai Master Controller
BW16 (RTL8720DN)	1	Wajib untuk fitur Deauth 5GHz/2.4GHz
NRF24L01+	2	Wajib untuk fitur Bluetooth Jammer
OLED SSD1306 128x64	1	I2C Address: 0x3C
Push Button	4	UP, DOWN, SELECT, BACK
Kapasitor 10uF	2	Ditempel di VCC NRF24L01
Wiring Kunci:

OLED: SDA -> GPIO 4, SCL -> GPIO 5
BW16: TX -> GPIO 26, RX -> GPIO 25
NRF #1 (HSPI): CE -> GPIO 16, CSN -> GPIO 15
NRF #2 (VSPI): CE -> GPIO 22, CSN -> GPIO 21
Buttons: UP -> GPIO 17, DOWN -> GPIO 33, SELECT -> GPIO 27, BACK -> GPIO 32
💎 Dapatkan Versi Full / Premium
File yang Anda lihat di repository ini adalah Versi Trial yang dibatasi hanya untuk demonstrasi awal.

Keuntungan Membeli Versi Premium:✅ Tidak Ada Batasan Waktu (Trial hanya 1 menit, Premium Unlimited).✅ Tidak Ada Lock EEPROM (Bisa diupgrade ke versi terbaru dikemudian hari).✅ Akses Update Selamanya (Fitur baru seperti Auto-Attack Sequence sedang dikembangkan).✅ Support Teknis via Telegram (Bantuan troubleshooting dan custom wiring).

🛒 Harga: [RP 50.000]
<img width="233" height="28" alt="image" src="https://github.com/user-attachments/assets/7a4dee06-ce5a-4dc1-9fd3-9eb36f2167ff" />


Klik tombol di atas untuk langsung chat dengan saya di Telegram.
📸 Preview & Dokumentasi
(Ganti link dibawah ini setelah Anda upload gambar ke repository)

Tampilan Web Dashboard:
Dashboard

Tampilan Wiring Modul:
Wiring

⚖️ Legal Disclaimer
PERINGATAN KERAS: Alat ini dibuat murni untuk Penetration Testing dan Educational Purpose dalam lingkup keamanan jaringan. Dilarang keras menggunakan tool ini untuk menyerang, mencuri data, atau merusak jaringan yang BUKAN milik Anda. Segala bentuk penyalahgunaan yang melanggar hukum negara Anda BUKAN merupakan tanggung jawab Developer. Dengan membeli firmware ini, Anda menyetujui syarat dan ketentuan ini.
Built with ❤️ by AETHERNET Developer Team
