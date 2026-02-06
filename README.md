# E-surat-ISTTS

**E-surat-ISTTS** adalah sistem manajemen dokumen berbasis web yang bertujuan untuk menyederhanakan administrasi kampus dengan mengintegrasikan alur kerja dokumen digital, meningkatkan efisiensi, serta mendukung kerangka pengembangan aplikasi berbasis internet.
---
## Role Utama dan Fitur Masing-masing
### 🧑‍🏫 1. Dosen
**Deskripsi:**  
Pengguna yang mengajukan surat tugas dan melampirkan surat undangan.
**Fitur:**
- 🔹 Login / Register (SSO / Email)
- 🔹 Dashboard Dosen: melihat status semua surat tugas (Diajukan, Diproses, Disetujui, Ditolak)
- 🔹 Ajukan Surat Tugas: isi form (tujuan, tanggal kegiatan, tempat, lampirkan surat undangan)
- 🔹 Lihat Riwayat Surat Tugas
- 🔹 Download Surat Tugas yang Disetujui (PDF)
- 🔹 Notifikasi otomatis (Email / Alert) ketika surat disetujui atau ditolak
**Isi Sidebar:**  
`DASHBOARD, RIWAYAT, AJUKAN SURAT TUGAS, LOGOUT`

---

### 2. Kaprodi
**Deskripsi:**  
Pihak pertama yang memverifikasi pengajuan dosen dalam satu program studi.
**Fitur:**
- 🔹 Lihat daftar pengajuan surat tugas dari dosen di prodi-nya
- 🔹 Review & ACC / Tolak permohonan
- 🔹 Ajukan Surat Tugas (sebagai Kaprodi)
- 🔹 Tambahkan catatan atau revisi jika ditolak
- 🔹 Histori keputusan
- 🔹 Forward otomatis ke Dekan setelah ACC
**Isi Sidebar:**  
`DASHBOARD, LIST PENGAJUAN SURAT, AJUKAN SURAT TUGAS, LOGOUT`

---

### 👨‍💼 3. Dekan Fakultas (FST / FD)
**Deskripsi:**  
Pihak yang memberikan persetujuan akhir untuk surat tugas fakultas.
**Fitur:**
- 🔹 Melihat daftar pengajuan surat tugas dari prodi di bawah fakultasnya
- 🔹 ACC / Tolak surat tugas
- 🔹 Membuat surat tugas sendiri (khusus Dekan)  
  → diarahkan langsung ke Rektor untuk tanda tangan, tetapi tetap melalui verifikasi Sekretaris
- 🔹 Memberikan tanda tangan digital setelah surat tugas dibuat oleh Sekretaris
- 🔹 Sistem otomatis mengirim notifikasi ke Sekretaris Rektor setelah tanda tangan digital
**Isi Sidebar:**  
`DASHBOARD, LIST PENGAJUAN SURAT, AJUKAN SURAT TUGAS, LOGOUT`

---

### 👩‍💼 4. Sekretaris Rektor / Sekretaris Fakultas
**Deskripsi:**  
Pusat pembuatan surat dan pengelolaan dokumen resmi kampus.
**Fitur Utama:**
- 🔹 Melihat daftar surat tugas yang sudah disetujui oleh Dekan
- 🔹 Generate surat tugas berdasarkan jenis kegiatan:
  - Surat Tugas Biasa (narasumber, peserta, pembicara, dll)
  - Surat Tugas Assesor BKD
- 🔹 Edit data surat sebelum di-generate menjadi PDF final
- 🔹 Generate Surat Tugas (PDF):
  - Menggunakan DomPDF
  - Nomor surat otomatis dari database (auto_increment), tanpa role BAA
- 🔹 Meneruskan surat ke Dekan untuk tanda tangan digital (atau ke Rektor jika diperlukan)
- 🔹 Histori surat tugas & surat keluar
- 🔹 Laporan surat tugas, surat masuk, dan surat keluar per bulan / fakultas / dosen (diagram / statistik)
**Isi Sidebar:**  
`DASHBOARD, LIST PENGAJUAN SURAT, LOGOUT`

---

### 🏛️ 5. Rektor
**Deskripsi:**  
Penandatangan tertinggi dan pemberi otorisasi surat tugas tertentu.
**Fitur:**
- 🔹 Melihat surat tugas dari Dekan atau surat tugas strategis
- 🔹 Memberikan tanda tangan digital (QR Code / e-Sign)
- 🔹 Melihat histori surat tugas fakultas
**Isi Sidebar:**  
`DASHBOARD, LIST PENGAJUAN SURAT, LOGOUT`

---

### 🧾 6. BAU (Biro Administrasi Umum)
**Deskripsi:**  
Mengurus stempel digital, transportasi, dan arsip surat tugas.
**Fitur:**
- 🔹 Melihat surat tugas yang sudah ditandatangani
- 🔹 Validasi & stempel digital (upload versi final + QR Code tanda tangan)
- 🔹 Upload versi final surat tugas ke sistem arsip (Google Drive API)
- 🔹 Laporan surat tugas, surat masuk, dan surat keluar per bulan / fakultas / dosen (diagram / statistik)
**Isi Sidebar:**  
`DASHBOARD, LIST PENGAJUAN SURAT, LOGOUT`

---

### 🛠️ 7. Admin Sistem
**Deskripsi:**  
Pengelola akun, role, dan konfigurasi sistem.
**Fitur:**
- 🔹 CRUD akun pengguna
- 🔹 Manajemen role & permission (Spatie Laravel Permission)
- 🔹 Monitoring log aktivitas (Spatie Activity Log)
- 🔹 Reset nomor surat tahunan dan pengaturan format bulan  
  (contoh: Januari kembali ke 001, Oktober = X)
**Isi Sidebar:**  
`DASHBOARD, USER, TEMPLATE SURAT, NOMOR SURAT, LOG AKTIVITAS, LOGOUT`

---

## Alur Sistem (New)

### 1. Surat tugas dibuat oleh dosen
Alur system New:
- surat tugas yang dibuat oleh dosen
dosen (create) > kaprodi (view & acc) > sekre (edit) > dekan (view & acc) > BAU (stempel)
- surat tugas yang dibuat oleh dekan untuk dirinya
dekan (create) > sekre (edit) > rektor (view & acc)
 
