# Tanya Baris — Forum Peer Tutor Koding
Dokumen Perancangan & Arsitektur Perangkat Lunak (Tugas Week 6 RPL)

## 1. Anggota Kelompok
1. (1251420006) - Wildan Kurniawan
2. (1251420145) - Muhammad Rafi Sya'bani
3. (1251420005) - Muhammad Alir Zikri
4. (1251420020) - Muhammad Haikal Fabian

## 2. Kebutuhan Utama Sistem (Requirements)
1. **R1 (Pengajuan Pertanyaan):** Mahasiswa dapat mengajukan pertanyaan baru lengkap dengan judul, kategori tag, deskripsi kendala, serta cuplikan kode.
2. **R2 (Tanggapan Peer Tutor):** Peer tutor dapat memberikan tanggapan atau solusi koding dengan penyorotan sintaks (*syntax highlighting*).
3. **R3 (Verifikasi Solusi):** Penanya dapat menandai salah satu tanggapan tutor sebagai "Solusi Terverifikasi" untuk menyelesaikan thread pertanyaan.
4. **R4 (Pencarian & Filter):** Pengguna dapat mencari pertanyaan berdasarkan kata kunci judul dan menyaring berdasarkan tag bahasa pemrograman (`Python`, `JavaScript`, `Java`, dll).


## 3. Daftar Modul & Tanggung Jawab
* **Modul Pertanyaan (*Question Module*):** Mengelola pembuatan pertanyaan baru, menampilkan daftar pertanyaan, serta menangani fitur pencarian dan filter tag.
* **Modul Tanggapan (*Answer Module*):** Mengelola pengisian jawaban dari peer tutor, perhitungan upvote, dan atribut pembuat jawaban.
* **Modul Verifikasi (*Verification Module*):** Mengatur perubahan status pertanyaan dari *open/answered* menjadi *solved* saat penanya memilih jawaban terbaik.
* **Modul Tampilan & Highlighter (*UI & Code Syntax Module*):** Menangani rendering antarmuka pengguna, switch tema (*Dark/Light mode*), serta parsing warna sintaks kode secara otomatis.

## 4. Diagram Arsitektur & Alur Fitur

### Alur Fitur Verifikasi Solusi
```mermaid
graph TD
    A[Penanya Membuka Detail Pertanyaan] --> B[Melihat Daftar Tanggapan dari Tutor]
    B --> C{Pilih Tanggapan yang Tepat?}
    C -- Ya --> D[Klik Tombol Tandai Solusi]
    C -- Tidak --> E[Tunggu Tanggapan Lain / Kirim Tanggapan Baru]
    D --> F[Sistem Memperbarui Status jadi 'Solusi Terverifikasi']
    F --> G[Tampilan Kartu Berubah Menjadi Solusi Terverifikasi]
