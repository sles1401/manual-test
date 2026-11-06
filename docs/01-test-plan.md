# Rencana Pengujian — OrangeHRM Demo

| Field | Nilai |
|---|---|
| Dokumen | Rencana Pengujian (Test Plan) |
| Versi | 1.0 |
| Tanggal | 2026-11-06 |
| Penulis | Suryani Lestari |
| Status | Final untuk desain; eksekusi belum dimulai |
| Aplikasi | OrangeHRM Open Source Demo (`https://opensource-demo.orangehrmlive.com/`) |
| Jenis | Portofolio QA — aplikasi demo publik |

## 1. Tujuan

Menetapkan ruang lingkup, strategi, dan kriteria keberhasilan pengujian manual
modul inti OrangeHRM Demo, sekaligus menjadi contoh artefak perencanaan QA yang
dapat ditinjau.

## 2. Latar belakang

OrangeHRM Demo menyediakan alur HRIS end-to-end: data karyawan, cuti, absensi,
rekrutmen, hingga administrasi pengguna. Karena data demo dipakai bersama publik,
pengujian harus memakai data uji yang unik dan tidak menghapus data milik orang
lain.

## 3. Ruang lingkup

| Termasuk | Tidak termasuk |
|---|---|
| Login, logout, dan proteksi sesi | Registrasi akun (tidak tersedia di demo) |
| Dashboard dan navigasi modul | Pengujian performa dan beban |
| PIM: tambah, cari, ubah, hapus karyawan | Integrasi email/SMS sungguhan |
| Leave: pengajuan, persetujuan, pembatalan | Perhitungan payroll |
| Time: punch in/out, timesheet | Modul Maintenance |
| Recruitment: lowongan, kandidat, interview | Pengujian keamanan (penetration testing) |
| My Info dan Admin (user, job title, location) | Pengujian mobile native |
| Directory | Aksesibilitas tingkat lanjut (WCAG audit penuh) |

## 4. Lingkungan pengujian

| Item | Detail |
|---|---|
| URL | `https://opensource-demo.orangehrmlive.com/` |
| Browser | Google Chrome versi stabil terbaru |
| Resolusi | 1366×768 dan 1920×1080 |
| Akun admin | `Admin` / `admin123` (kredensial demo publik) |
| Akun ESS | Dibuat selama eksekusi melalui menu Admin |
| Data uji | Karyawan, lowongan, dan kandidat dengan prefix `QA-` + tanggal |
| Bukti | Screenshot dan log disimpan di [`evidence/`](../evidence/) |

## 5. Strategi pengujian

Pendekatan **risk-based manual testing**: modul dengan dampak terbesar ke data
karyawan dan proses persetujuan diuji lebih dulu.

Teknik desain yang dipakai:

- **Equivalence partitioning** — memisahkan input valid dan tidak valid.
- **Boundary value analysis** — panjang input, batas tanggal cuti, jam timesheet.
- **Decision table** — kombinasi role dan akses menu.
- **State transition** — status cuti, timesheet, dan tahapan kandidat.
- **Error guessing** — field wajib, duplikasi ID, dan aksi destruktif.
- **Session-based exploratory testing** — charter per modul, timebox 60–90 menit.

Urutan eksekusi:

1. **Smoke test** — login dan navigasi seluruh modul.
2. **Functional test** — test case P1 per modul.
3. **Negative dan boundary test** — test case P2/P3.
4. **Regression** — ulangi P1 setelah perubahan data atau setelah bug diperbaiki.
5. **Exploratory** — sesi bebas terarah untuk menemukan risiko yang belum tercakup.

## 6. Jenis pengujian

| Jenis | Fokus |
|---|---|
| Functional | Alur bisnis berjalan sesuai kebutuhan |
| Negative | Validasi input dan penanganan kesalahan |
| UI/UX | Konsistensi layout, label, dan umpan balik |
| Regression | Fitur lama tetap berjalan setelah perubahan |
| Exploratory | Risiko yang tidak tertangkap skrip formal |

## 7. Entry criteria

- Aplikasi demo dapat diakses dan halaman login tampil.
- Kredensial admin valid.
- Test case untuk modul yang diuji sudah ditinjau.
- Data uji unik sudah disiapkan.
- Folder bukti dan format penamaan sudah disepakati.

## 8. Exit criteria

- Seluruh test case P1 sudah dieksekusi.
- Minimal 95% test case P1 dan P2 dieksekusi.
- Tidak ada defect terbuka severity **Critical** atau **High**.
- Defect yang tersisa sudah didokumentasikan dengan workaround.
- Test Summary Report terisi dan ditinjau.

## 9. Kriteria suspend dan resume

**Suspend** jika login tidak bisa diakses, data demo rusak massal, atau lingkungan
tidak stabil lebih dari 30 menit.

**Resume** setelah lingkungan pulih dan smoke test ulang lulus.

## 10. Deliverables

- Test plan (dokumen ini)
- Test case per modul
- Bug report untuk setiap temuan terverifikasi
- Catatan exploratory testing
- Test summary report
- Bukti screenshot/log

## 11. Peran dan tanggung jawab

| Peran | Tanggung jawab |
|---|---|
| QA Engineer (Suryani Lestari) | Perencanaan, desain kasus, eksekusi, pelaporan, retest |
| Reviewer | Meninjau cakupan dan kejelasan langkah reproduksi |

## 12. Jadwal (relatif)

| Hari | Aktivitas |
|---|---|
| Hari 1 | Setup lingkungan, smoke test, finalisasi data uji |
| Hari 2–4 | Eksekusi test case P1 dan P2 per modul |
| Hari 5 | Eksekusi P3, exploratory session, regression P1 |
| Hari 6 | Retest defect, isi summary report, tinjauan akhir |

## 13. Risiko dan mitigasi

| Risiko | Dampak | Mitigasi |
|---|---|---|
| Data demo diubah pengguna lain | Hasil tidak konsisten | Pakai data unik berprefix `QA-`, catat waktu eksekusi |
| Demo di-reset sewaktu-waktu | Data uji hilang | Simpan bukti segera setelah langkah kritis |
| Kredensial demo berubah | Tidak bisa login | Catat kegagalan sebagai blocked, cek pengumuman demo |
| Perhitungan cuti bergantung konfigurasi | Ekspektasi meleset | Verifikasi entitlement sebelum menilai hasil |
| Waktu eksekusi terbatas | Cakupan tidak penuh | Prioritaskan P1, catat sisa kasus sebagai not run |

## 14. Alat

- Browser Chrome dan DevTools (console, network, responsive mode)
- Google Sheets untuk data uji sementara
- Screenshot tool bawaan OS
- Repositori ini untuk dokumentasi

## 15. Dokumen terkait

- [Test Cases](02-test-cases.md)
- [Bug Reports](03-bug-reports.md)
- [Exploratory Notes](04-exploratory-notes.md)
- [Test Summary Report](05-test-summary-report.md)
- [Traceability Matrix](06-traceability-matrix.md)
