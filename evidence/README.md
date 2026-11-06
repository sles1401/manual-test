# Evidence

Folder ini menyimpan bukti eksekusi: screenshot, rekaman, dan log. Belum ada bukti
karena pengujian belum dijalankan.

## Konvensi penamaan

```text
<test-case-id>_<deskripsi-singkat>_<YYYYMMDD>.<ext>
```

Contoh:

```text
LGN-02_invalid-credentials_20261106.png
PIM-03_duplicate-employee-id_20261106.png
TIM-04_timesheet-submitted_20261106.png
```

## Yang perlu dibuktikan

| Jenis kasus | Bukti minimal |
|---|---|
| Pass | Screenshot hasil akhir yang menunjukkan status atau data benar |
| Fail | Screenshot hasil aktual + langkah yang sudah dicoba |
| Blocked | Screenshot pesan error atau kondisi yang menghalangi |
| UI | Screenshot pada resolusi yang diuji |

## Aturan

- Potong screenshot agar hanya menampilkan area relevan.
- Jangan menyertakan data pribadi, token, atau kredensial selain akun demo publik.
- Simpan bukti segera setelah langkah kritis; data demo bisa berubah.
- Sebutkan nama file bukti pada laporan bug dan catatan exploratory.
