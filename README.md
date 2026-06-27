# FiveM Server Repository (QBCore Framework)

Repositori ini berisi server data dan resources untuk server FiveM berbasis framework QBCore.

---

## 📂 Struktur Project

- `txData/QBCore_1D0140.base/` - **(Di-track di Git)** Folder utama yang berisi resources, scripts, dan konfigurasi server.
  - `resources/` - Tempat semua script (QBCore, standalone, voice, dsb.) berada.
  - `server.cfg` - Konfigurasi utama server.
- `server/` - **(Di-ignore)** Berisi server artifacts (FXServer engine binaries).
- `txData/default/` - **(Di-ignore)** Pengaturan txAdmin lokal Anda.

---

## 🚀 Panduan Setup & Instalasi (Untuk Pengguna Baru / Clone)

Jika Anda melakukan clone repositori ini ke komputer Anda, ikuti langkah-langkah di bawah ini untuk menjalankannya secara lokal.

### 1. Prasyarat (Prerequisites)
Sebelum memulai, pastikan Anda sudah menginstal:
* [Git](https://git-scm.com/)
* [XAMPP](https://www.apachefriends.org/) atau [HeidiSQL](https://www.heidisql.com/) / MySQL Server untuk database.

### 2. Clone Repositori
Clone project ini ke folder pilihan Anda:
```bash
git clone <URL_REPO_ANDA>
cd kotabelajar
```

### 3. Unduh Server Artifacts (FXServer)
Karena server artifacts (file engine exe dan dll) tidak di-track di Git karena ukurannya yang besar, Anda harus mengunduhnya secara manual:
1. Kunjungi [FiveM Artifacts Server](https://runtime.fivem.net/artifacts/fivem/build_server_windows/master/).
2. Unduh versi **Latest Recommended** (paling stabil).
3. Buat folder baru bernama `server` di root project Anda (`kotabelajar/server`).
4. Ekstrak seluruh isi file zip/7z server artifacts yang telah diunduh ke dalam folder `server` tersebut.

### 4. Setup Database
1. Jalankan MySQL Server Anda (misal lewat XAMPP control panel klik *Start* pada MySQL).
2. Buat database baru dengan nama sesuai konfigurasi Anda (secara default biasanya bernama `qbold` atau `qbcore`).
3. Import file database sql (jika ada SQL backup di dalam resources Anda) atau biarkan QBCore membuat tabelnya secara otomatis saat dijalankan pertama kali (QBCore modern mendukung otomatisasi pembuatan tabel via oxmysql).

### 5. Setup file `server.cfg`
Buka file `txData/QBCore_1D0140.base/server.cfg` dan sesuaikan variabel berikut:
* **Database Connection String**:
  ```cfg
  set mysql_connection_string "user=root;database=nama_db_kamu;password=password_kamu"
  ```
* **License Key & Steam Web API**:
  Dapatkan key Anda sendiri dan ganti baris berikut (jangan pernah membagikan/men-commit key pribadi Anda ke publik!):
  ```cfg
  sv_licenseKey "MASUKKAN_LICENSE_KEY_FIVEM_DISINI"
  set steam_webApiKey "MASUKKAN_STEAM_API_KEY_DISINI"
  ```

### 6. Jalankan Server via txAdmin
1. Buka folder `server/` dan jalankan `FXServer.exe`.
2. Halaman browser txAdmin akan otomatis terbuka (atau akses melalui `http://localhost:40120/`).
3. Masukkan PIN yang tertera di konsol CMD untuk masuk.
4. Pada setup txAdmin, pilih opsi **Local Server Data** (Existing Server Data).
5. Atur path ke server data ke: `C:\path\to\your\kotabelajar\txData\QBCore_1D0140.base` (sesuaikan dengan lokasi folder hasil clone Anda).
6. Tentukan path file konfigurasi ke: `C:\path\to\your\kotabelajar\txData\QBCore_1D0140.base\server.cfg`.
7. Selesaikan setup dan klik **Start Server**.
