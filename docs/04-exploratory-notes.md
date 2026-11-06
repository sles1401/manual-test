# Exploratory Notes — OrangeHRM Demo

Catatan sesi **session-based exploratory testing**. Setiap sesi punya charter,
timebox, dan catatan hasil; temuan yang layak dilaporkan dipindahkan ke
[Bug Reports](03-bug-reports.md).

## Heuristik yang dipakai (SFDPOT)

| Huruf | Fokus | Contoh pertanyaan |
|---|---|---|
| S — Structure | Struktur produk | Apakah navigasi dan hierarki menu konsisten? |
| F — Function | Fungsi | Apakah setiap tombol melakukan apa yang tertulis? |
| D — Data | Data | Bagaimana perilaku dengan input kosong, duplikat, atau sangat panjang? |
| P — Platform | Lingkungan | Apakah layout tetap baik di resolusi berbeda? |
| O — Operations | Operasi | Apa yang terjadi saat aksi dilakukan berulang atau bersamaan? |
| T — Time | Waktu | Bagaimana perilaku tanggal lampau, rentang terbalik, atau zona waktu? |

## Charter sesi

| ID | Charter | Area | Timebox | Fokus heuristik |
|---|---|---|---|---|
| EXP-01 | Jelajahi alur tambah karyawan untuk menemukan celah validasi | PIM | 60 menit | D, O |
| EXP-02 | Uji konsistensi pesan error dan field wajib di seluruh form | Global | 60 menit | S, F |
| EXP-03 | Jelajahi transisi status cuti dari pengajuan sampai pembatalan | Leave | 90 menit | F, T |
| EXP-04 | Uji perilaku timesheet saat data diisi berulang dan melebihi batas | Time | 60 menit | D, O |
| EXP-05 | Jelajahi perbedaan tampilan dan akses antara admin dan ESS | Admin | 60 menit | S, F |
| EXP-06 | Uji alur rekrutmen dari lowongan sampai penjadwalan interview | Recruitment | 90 menit | F, T |

## Template catatan sesi

```markdown
### Sesi EXP-XX — [Tanggal] — [Tester]

| Field | Nilai |
|---|---|
| Charter | |
| Area | |
| Timebox | |
| Build / lingkungan | |
| Durasi aktual | |
| Status | Selesai / Terhenti |

**Cakupan yang dijelajahi**
- 

**Yang berjalan baik**
- 

**Yang mencurigakan**
- 

**Temuan**
| Temuan | Bukti | Tindak lanjut |
|---|---|---|
| | | |

**Risiko yang belum tercakup**
- 

**Ide sesi berikutnya**
- 
```

## Log sesi

| ID | Tanggal | Area | Durasi | Temuan | Status |
|---|---|---|---|---|---|
| EXP-01 | — | PIM | — | — | Belum dijalankan |
| EXP-02 | — | Global | — | — | Belum dijalankan |
| EXP-03 | — | Leave | — | — | Belum dijalankan |
| EXP-04 | — | Time | — | — | Belum dijalankan |
| EXP-05 | — | Admin | — | — | Belum dijalankan |
| EXP-06 | — | Recruitment | — | — | Belum dijalankan |

## Catatan

- Hentikan sesi jika menemukan defect **S1**; dokumentasikan lalu lanjutkan
  setelah defect tersebut ditangani atau dijadikan known issue.
- Simpan bukti segera; data demo bisa berubah kapan saja.
- Satu sesi fokus pada satu charter agar hasilnya bisa dibandingkan.
