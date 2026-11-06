# Bug Reports — OrangeHRM Demo

Dokumen ini menjelaskan cara melaporkan defect dan menyimpan daftar temuan yang
sudah terverifikasi. **Belum ada defect terverifikasi** sampai sesi eksekusi
dijalankan; tabel di bagian akhir sengaja kosong.

## Severity

| Level | Nama | Definisi |
|---|---|---|
| S1 | Critical | Alur utama tidak bisa dipakai, data hilang, atau akses tanpa otorisasi |
| S2 | High | Fitur penting gagal tanpa workaround yang wajar |
| S3 | Medium | Fitur berjalan tetapi hasil salah pada kondisi tertentu; ada workaround |
| S4 | Low | Masalah kosmetik, typo, atau ketidaknyamanan kecil |

## Priority

| Level | Nama | Definisi |
|---|---|---|
| P1 | Urgent | Harus diperbaiki sebelum rilis |
| P2 | High | Perbaikan dijadwalkan pada siklus berikutnya |
| P3 | Medium | Dapat ditunda tanpa menghambat alur utama |
| P4 | Low | Perbaikan opsional |

Severity menilai **dampak teknis**, priority menilai **urutan perbaikan**. Defect
kosmetik bisa berpriority tinggi jika muncul di halaman utama, dan sebaliknya.

## Template laporan

```markdown
### BUG-XXX — [Judul singkat dan spesifik]

| Field | Nilai |
|---|---|
| Modul | |
| Lingkungan | Chrome [versi] / [resolusi] / OrangeHRM Demo |
| Severity | S1–S4 |
| Priority | P1–P4 |
| Status | Open / In Progress / Fixed / Retest / Closed |
| Pelapor | |
| Tanggal | YYYY-MM-DD |

**Prasyarat**
- 

**Langkah reproduksi**
1. 
2. 
3. 

**Hasil aktual**
- 

**Hasil yang diharapkan**
- 

**Tingkat reproduksi**
Selalu / Sering / Kadang (x dari y percobaan)

**Bukti**
- [Nama file di evidence/]()

**Catatan tambahan**
- 
```

## Aturan penulisan

- Satu laporan untuk satu defect; jangan gabungkan beberapa masalah.
- Tulis langkah yang bisa diikuti orang lain tanpa pengetahuan tambahan.
- Jelaskan hasil aktual dan hasil yang diharapkan secara terpisah.
- Sertakan bukti screenshot atau rekaman bila memungkinkan.
- Jangan menyertakan data pribadi atau kredensial selain akun demo publik.
- Setelah diperbaiki, lakukan retest dan ubah status menjadi `Closed` atau
  `Reopened` disertai catatan.

## Contoh format (fiktif)

> Contoh di bawah hanya menunjukkan struktur laporan, **bukan temuan nyata**
> terhadap OrangeHRM.

### BUG-XXX — Tombol Save tetap aktif saat field wajib kosong

| Field | Nilai |
|---|---|
| Modul | Contoh |
| Lingkungan | Chrome 140 / 1366×768 / OrangeHRM Demo |
| Severity | S3 |
| Priority | P3 |
| Status | Open |
| Pelapor | Suryani Lestari |
| Tanggal | YYYY-MM-DD |

**Prasyarat**
- Login sebagai admin.

**Langkah reproduksi**
1. Buka halaman formulir contoh.
2. Kosongkan field wajib.
3. Klik **Save**.

**Hasil aktual**
- Formulir tersimpan tanpa validasi.

**Hasil yang diharapkan**
- Pesan `Required` tampil dan data tidak tersimpan.

**Tingkat reproduksi**
Selalu (3 dari 3 percobaan)

**Bukti**
- `contoh-form-kosong.png`

## Daftar temuan terverifikasi

| ID | Judul | Modul | Severity | Priority | Status | Test case |
|---|---|---|---|---|---|---|
| — | Belum ada temuan terverifikasi | — | — | — | — | — |

## Ringkasan defect (isi setelah eksekusi)

| Severity | Open | Fixed | Closed | Total |
|---|---|---|---|---|
| S1 Critical | 0 | 0 | 0 | 0 |
| S2 High | 0 | 0 | 0 | 0 |
| S3 Medium | 0 | 0 | 0 | 0 |
| S4 Low | 0 | 0 | 0 | 0 |
| **Total** | **0** | **0** | **0** | **0** |
