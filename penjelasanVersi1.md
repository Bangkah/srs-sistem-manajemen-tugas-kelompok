# Dokumentasi Flowchart & Database
## Sistem Manajemen Tugas Kelompok

Dokumen ini menjelaskan keterkaitan antara **alur sistem (flowchart)** dan **database**.  
Setiap modul dijelaskan berdasarkan bagaimana user berinteraksi dengan sistem, lalu data apa saja yang disimpan.
#### mohon untuk teman teman dapat memahaminya
*shit mohon wak*

---

## 1. AUTH (Login & Registrasi)

### Flowchart
- User baru melakukan registrasi → data tersimpan ke database.  
- User login menggunakan email & password.  
- Sistem memvalidasi:
  - Jika valid → masuk dashboard.  
  - Jika tidak valid → ulangi login.  

### Database
- **users**
  - Menyimpan data user (nama, email, password).  
  - `role` menentukan peran: **ketua** atau **anggota**.  
  - Tersedia kolom `created_at`, `updated_at` untuk pencatatan waktu.  

Semua aktivitas login & registrasi merujuk ke tabel ini.  

---

## 2. GROUP (Manajemen Kelompok)

### Flowchart
- Ketua membuat kelompok baru.  
- Ketua mengundang anggota.  
- Anggota menerima undangan dan bergabung.  
- Alternatif: anggota masuk menggunakan kode undangan.  

### Database
- **groups**
  - Menyimpan informasi kelompok (nama, deskripsi, pembuat).  

- **group_members**
  - Relasi many-to-many antara `users` dan `groups`.  
  - Ada kolom:
    - `role` (ketua / anggota di dalam kelompok).  
    - `status` (pending = diundang, active = sudah bergabung).  

Dengan ini:  
- Satu user bisa ikut banyak kelompok.  
- Satu kelompok bisa punya banyak user.  

---

## 3. PROJECT (Manajemen Proyek)

### Flowchart
- Ketua atau anggota membuat proyek di dalam kelompok.  
- Proyek terkait dengan 1 kelompok.  
- Tiap kelompok bisa punya banyak proyek.  

### Database
- **projects**
  - Menyimpan data proyek dalam kelompok.  
  - Kolom penting:
    - `group_id` → relasi ke kelompok.  
    - `created_by` → siapa pembuat proyek.  

---

## 4. TASK (Manajemen Tugas)

### Flowchart
- Ketua menambahkan tugas di dalam proyek.  
- Tugas di-*assign* ke anggota tertentu.  
- Anggota mengerjakan dan mengubah status (*to-do → in-progress → done*).  
- Anggota upload hasil + catatan pengerjaan.  
- Ketua melakukan review:
  - Jika disetujui → progress proyek naik.  
  - Jika ditolak → tugas kembali ke status pengerjaan.  

### Database
- **tasks**
  - Menyimpan detail tugas (judul, deskripsi, status, deadline, assigned_to).  

- **task_submissions**
  - Menyimpan hasil pengerjaan tugas.  
  - Ada:
    - `file_url` (lampiran hasil kerja).  
    - `note` (catatan pengerjaan).  
    - `review_status` (pending, approved, rejected).  

---

## 5. COLLAB (Kolaborasi & Diskusi)

### Flowchart
- Anggota memberi komentar pada tugas.  
- Komentar memicu notifikasi untuk anggota lain.  
- Riwayat komentar tersimpan.  
- Anggota juga bisa upload file tambahan yang dapat diunduh anggota lain.  

### Database
- **comments**
  - Menyimpan komentar terkait tugas.  

- **attachments**
  - Menyimpan file tambahan dari anggota.  

Semua komentar & lampiran selalu terkait ke **satu tugas tertentu**.  

---

## 6. REPORT (Monitoring & Laporan)

### Flowchart
- Ketua membuka menu laporan proyek.  
- Sistem menghitung progress otomatis berdasarkan status semua tugas.  
- Progress ditampilkan dalam bentuk persentase + grafik kontribusi anggota.  

### Database
- **reports**
  - Menyimpan laporan proyek.  
  - Ada:
    - `progress` (%).  
    - `details` (catatan tambahan).  
    - `generated_at` (waktu laporan dibuat).  

---

## Ringkasan Alur Keseluruhan

1. User registrasi → login.  
2. Ketua membuat kelompok → undang anggota.  
3. Dalam kelompok → buat proyek.  
4. Dalam proyek → buat tugas.  
5. Tugas → dikerjakan anggota → upload hasil → direview ketua.  
6. Sistem menghitung progress → tampilkan di laporan.  
7. Komentar & lampiran mendukung kolaborasi antar anggota.  

---
