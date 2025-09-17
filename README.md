# Software Requirement Specification (SRS)

**Sistem Manajemen Tugas Kelompok**

---

## 1. Pendahuluan

### 1.1 Tujuan

Dokumen ini disusun untuk menjelaskan kebutuhan perangkat lunak sistem manajemen kerja kelompok berbasis web (Laravel). Sistem ini akan membantu mahasiswa, dosen, atau anggota organisasi dalam:

* Membentuk kelompok
* Membuat dan mengelola proyek
* Membagi tugas
* Melakukan kolaborasi (komentar, unggah berkas)
* Memantau progress proyek

### 1.2 Lingkup Sistem

Sistem ini akan dikembangkan menggunakan **Laravel + Tailwind CSS**, dengan basis data relasional (MySQL). Sistem dapat diakses melalui browser.
Lingkup utama sistem:

* Registrasi dan autentikasi pengguna
* Manajemen kelompok (buat, gabung, keluar)
* Manajemen proyek dalam kelompok
* Manajemen tugas dalam proyek
* Komunikasi lewat komentar dan unggahan file
* Monitoring progress proyek secara real-time

### 1.3 Definisi, Singkatan, dan Akronim

* **User**: Pengguna sistem (mahasiswa/dosen/anggota organisasi).
* **Admin**: Pengguna dengan hak akses khusus (misalnya ketua kelompok).
* **Group**: Kelompok kerja yang berisi beberapa user.
* **Project**: Pekerjaan besar yang dikerjakan oleh sebuah kelompok.
* **Task**: Pekerjaan kecil yang merupakan bagian dari project.

---

## 2. Deskripsi Umum

### 2.1 Perspektif Produk

Produk ini merupakan aplikasi web kolaborasi mirip Trello/Asana namun difokuskan untuk kebutuhan akademik/kelompok belajar.

### 2.2 Fungsi Utama

1. **Manajemen Pengguna**

   * Registrasi, login, reset password
   * Role: admin, ketua, anggota
2. **Manajemen Kelompok**

   * Membuat kelompok
   * Mengundang anggota (via email/link join)
   * Mengatur peran anggota (ketua/anggota)
3. **Manajemen Proyek**

   * Membuat proyek baru dalam kelompok
   * Menetapkan deadline dan deskripsi
   * Memantau progress proyek
4. **Manajemen Tugas**

   * Membuat, mengupdate, dan menghapus tugas
   * Memberi prioritas dan deadline
   * Menugaskan ke anggota tertentu
   * Update status (*todo, in-progress, done*)
5. **Kolaborasi**

   * Komentar pada tugas
   * Upload lampiran (dokumen/gambar)
6. **Monitoring & Laporan**

   * Progress proyek berdasarkan tugas selesai
   * Riwayat aktivitas anggota

### 2.3 Karakteristik Pengguna

* **Mahasiswa**: sebagai anggota kelompok belajar
* **Dosen/Pembimbing**: bisa menjadi admin/observer
* **Organisasi/Lembaga**: sebagai admin untuk memantau progress

### 2.4 Batasan

* Sistem berbasis web, akses via browser
* Autentikasi berbasis email & password
* File upload dibatasi ukuran tertentu (misalnya 10MB)
* Progress dihitung otomatis berdasarkan jumlah tugas yang selesai

---

## 3. Kebutuhan Fungsional

### 3.1 Modul Pengguna

* User dapat mendaftar, login, logout
* User dapat memperbarui profil
* User dapat bergabung dalam satu atau lebih kelompok

### 3.2 Modul Kelompok

* Ketua membuat kelompok
* Anggota dapat menerima undangan
* Ketua dapat menghapus anggota

### 3.3 Modul Proyek

* Ketua membuat proyek dalam kelompok
* Anggota dapat melihat proyek
* Ketua/anggota yang berwenang dapat menambah/menghapus proyek

### 3.4 Modul Tugas

* User membuat tugas pada proyek
* Tugas memiliki status, prioritas, deadline
* Tugas dapat ditugaskan ke anggota

### 3.5 Modul Komentar & Lampiran

* User menambahkan komentar di tugas
* User mengunggah file sebagai lampiran

### 3.6 Modul Monitoring

* Progress proyek dihitung otomatis
* Ketua dapat melihat laporan progress

---

## 4. Kebutuhan Non-Fungsional

* **Kinerja**: Sistem mampu menangani 100 user aktif bersamaan
* **Keamanan**: Autentikasi & otorisasi berbasis role
* **Portabilitas**: Dapat dijalankan di Desktop/Mobile
* **Usability**: Antarmuka sederhana, responsif (Tailwind CSS)
* **Reliabilitas**: Mendukung backup database

---

## 5. Model Data

Mengacu pada ERD/dbdiagram:

* Tabel utama: `users`, `groups`, `group_user`, `projects`, `tasks`, `comments`, `attachments`.

---

## 6. Antarmuka

* **UI/UX** dibuat dengan Tailwind CSS
* Tampilan responsif (desktop & mobile)
* Dashboard utama menampilkan daftar kelompok, proyek, dan tugas


