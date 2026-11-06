# Manual Testing Portfolio — OrangeHRM Demo

Portofolio pengujian manual oleh **Suryani Lestari**, QA Engineer. Repositori ini
mendokumentasikan perencanaan, desain kasus uji, dan pelaporan pengujian untuk
[OrangeHRM Open Source Demo](https://opensource-demo.orangehrmlive.com/) —
aplikasi HRIS publik yang biasa dipakai untuk latihan QA.

> **Disclaimer.** OrangeHRM adalah produk OrangeHRM Inc. Repositori ini tidak
> berafiliasi dengan OrangeHRM. Demo publik hanya dipakai sebagai objek latihan,
> dan seluruh data di dalamnya bersifat sementara.

## Status

| Field | Nilai |
|---|---|
| Fase | Desain pengujian selesai; eksekusi belum dijalankan |
| Versi dokumen | 1.0 |
| Terakhir diperbarui | 2026-11-06 |
| Lingkungan | Chrome desktop, OrangeHRM Open Source Demo |

Kolom **Status** pada test case masih `Belum dijalankan`. Hasil eksekusi dan bukti
akan diisi setelah benar-benar diuji — bukan diklaim lebih dulu.

## Ruang lingkup

Modul yang dicakup: Login & Autentikasi, Dashboard, PIM, Leave, Time, Recruitment,
My Info, Admin, dan Directory.

Tidak termasuk: pengujian performa/beban, penetration testing, integrasi email/SMS
sungguhan, dan modul Maintenance.

## Dokumen

| Dokumen | Isi |
|---|---|
| [01 — Test Plan](docs/01-test-plan.md) | Tujuan, ruang lingkup, strategi, entry/exit criteria, risiko |
| [02 — Test Cases](docs/02-test-cases.md) | 62 kasus uji manual per modul |
| [03 — Bug Reports](docs/03-bug-reports.md) | Panduan severity/priority, template, dan contoh format |
| [04 — Exploratory Notes](docs/04-exploratory-notes.md) | Charter session-based testing dan catatan sesi |
| [05 — Test Summary Report](docs/05-test-summary-report.md) | Template laporan hasil eksekusi dan metrik |
| [06 — Traceability Matrix](docs/06-traceability-matrix.md) | Pemetaan modul ke test case |
| [evidence/](evidence/) | Konvensi penamaan screenshot dan log |

## Cara membaca

1. Mulai dari **test plan** untuk memahami cakupan dan pendekatan.
2. **Test case** menunjukkan teknik desain: happy path, boundary, negatif, dan
   state transition.
3. **Bug report** menunjukkan format temuan yang bisa direproduksi.
4. **Summary report** diisi setelah sesi eksekusi selesai.

## Penulis

**Suryani Lestari** — QA Engineer, Bandung, Indonesia.

[GitHub](https://github.com/sles1401) · [Linktree](https://linktr.ee/sles1401)
