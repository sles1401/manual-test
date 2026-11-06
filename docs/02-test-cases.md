# Test Cases — OrangeHRM Demo

Desain kasus uji manual untuk modul inti OrangeHRM Demo. Seluruh kasus berstatus
**Belum dijalankan** sampai sesi eksekusi benar-benar dilakukan; hasilnya dicatat
di [Test Summary Report](05-test-summary-report.md).

## Legenda

| Kode | Arti |
|---|---|
| P1 | Kritis — alur utama, wajib lulus |
| P2 | Tinggi — fitur penting |
| P3 | Sedang — edge case atau UI |
| F | Fungsional |
| N | Negatif |
| U | UI/UX |
| R | Regresi |

Status yang dipakai saat eksekusi: `Belum dijalankan`, `Pass`, `Fail`, `Blocked`.
Untuk `Fail`, tautkan ID bug dari [Bug Reports](03-bug-reports.md).

## Ringkasan

| Modul | Jumlah | Rentang ID |
|---|---|---|
| Login & Autentikasi | 9 | LGN-01 – LGN-09 |
| Dashboard | 5 | DSH-01 – DSH-05 |
| PIM | 10 | PIM-01 – PIM-10 |
| Leave | 8 | LVE-01 – LVE-08 |
| Time | 6 | TIM-01 – TIM-06 |
| Recruitment | 7 | REC-01 – REC-07 |
| My Info | 5 | MYI-01 – MYI-05 |
| Admin | 9 | ADM-01 – ADM-09 |
| Directory | 3 | DIR-01 – DIR-03 |
| **Total** | **62** | |

## Login & Autentikasi

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| LGN-01 | Login dengan kredensial valid | Akun admin demo aktif | 1. Buka URL demo.<br>2. Isi `Admin` / `admin123`.<br>3. Klik **Login**. | Dashboard tampil dan menu profil menunjukkan `Admin`. | P1 | F | Belum dijalankan |
| LGN-02 | Login dengan password salah | — | 1. Isi `Admin` / `salah123`.<br>2. Klik **Login**. | Pesan `Invalid credentials` tampil; tetap di halaman login. | P1 | N | Belum dijalankan |
| LGN-03 | Login dengan kedua field kosong | — | 1. Kosongkan username dan password.<br>2. Klik **Login**. | Pesan `Required` tampil di kedua field; login tidak diproses. | P1 | N | Belum dijalankan |
| LGN-04 | Username kosong, password terisi | — | 1. Kosongkan username, isi password.<br>2. Klik **Login**. | `Required` hanya di username; login gagal. | P2 | N | Belum dijalankan |
| LGN-05 | Password kosong, username terisi | — | 1. Isi username, kosongkan password.<br>2. Klik **Login**. | `Required` hanya di password; login gagal. | P2 | N | Belum dijalankan |
| LGN-06 | Buka alur forgot password | — | 1. Klik link **Forgot your password?** | Halaman reset password tampil dengan field username dan tombol reset. | P3 | F | Belum dijalankan |
| LGN-07 | Akses URL terproteksi tanpa sesi | Browser incognito | 1. Buka `/web/index.php/pim/viewEmployeeList` tanpa login. | Diarahkan kembali ke halaman login; data tidak tampil. | P1 | N | Belum dijalankan |
| LGN-08 | Logout dan tombol Back | Sudah login | 1. Klik menu profil > **Logout**.<br>2. Tekan tombol Back browser. | Kembali ke halaman login; tombol Back tidak membuka dashboard. | P1 | F | Belum dijalankan |
| LGN-09 | Password disamarkan | — | 1. Ketik password di field password. | Karakter tampil sebagai titik dan tidak terbaca sebagai teks biasa. | P2 | U | Belum dijalankan |

## Dashboard

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| DSH-01 | Widget utama tampil | Login sebagai admin | 1. Buka Dashboard. | Widget Time at Work, My Actions, Quick Launch, Buzz Latest Posts, Employees on Leave Today, Employee Distribution, dan Legend tampil. | P1 | F | Belum dijalankan |
| DSH-02 | Navigasi dari Quick Launch | Login sebagai admin | 1. Klik **Apply Leave** di Quick Launch. | Halaman Apply Leave terbuka sesuai menu. | P2 | F | Belum dijalankan |
| DSH-03 | Tautan My Actions | Login sebagai admin | 1. Klik item atau angka pada widget My Actions. | Halaman daftar aksi terkait (Leave List atau Timesheet) terbuka. | P3 | F | Belum dijalankan |
| DSH-04 | Status Time at Work | Login sebagai admin | 1. Perhatikan widget Time at Work sebelum dan sesudah punch in. | Status dan tombol berubah sesuai kondisi attendance hari ini. | P3 | F | Belum dijalankan |
| DSH-05 | Layout pada 1366×768 | Login sebagai admin | 1. Set resolusi 1366×768.<br>2. Amati dashboard. | Tidak ada horizontal scroll; widget tidak tumpang tindih. | P2 | U | Belum dijalankan |

## PIM

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| PIM-01 | Tambah karyawan dengan field wajib | Login sebagai admin | 1. PIM > **Add Employee**.<br>2. Isi first, middle, last name.<br>3. Simpan. | Toast sukses tampil; karyawan muncul di Employee List. | P1 | F | Belum dijalankan |
| PIM-02 | Tambah karyawan tanpa first name | Login sebagai admin | 1. PIM > Add Employee.<br>2. Isi last name saja.<br>3. Simpan. | `Required` tampil di First Name; data tidak tersimpan. | P1 | N | Belum dijalankan |
| PIM-03 | Employee ID duplikat | Sudah ada karyawan uji | 1. Add Employee.<br>2. Isi Employee ID yang sudah dipakai.<br>3. Simpan. | Pesan `Employee Id already exists`; data tidak tersimpan. | P2 | N | Belum dijalankan |
| PIM-04 | Unggah foto karyawan | Login sebagai admin | 1. Add Employee.<br>2. Unggah JPG kurang dari 1 MB.<br>3. Simpan. | Preview foto tampil dan foto tersimpan setelah reload. | P2 | F | Belum dijalankan |
| PIM-05 | Cari karyawan berdasarkan nama | Karyawan uji sudah ada | 1. Buka Employee List.<br>2. Ketik nama karyawan uji.<br>3. Klik Search. | Hasil hanya menampilkan karyawan yang cocok. | P1 | F | Belum dijalankan |
| PIM-06 | Pencarian tanpa hasil | Login sebagai admin | 1. Cari nama acak yang tidak ada. | Pesan `No Records Found` tampil. | P2 | N | Belum dijalankan |
| PIM-07 | Ubah personal details | Karyawan uji sudah ada | 1. Buka karyawan > Personal Details.<br>2. Ubah last name.<br>3. Simpan, lalu reload. | Toast sukses tampil dan nilai baru tetap ada setelah reload. | P1 | F | Belum dijalankan |
| PIM-08 | Email tidak valid di contact details | Karyawan uji sudah ada | 1. Buka Contact Details.<br>2. Isi email `qa-test` tanpa domain.<br>3. Simpan. | Pesan validasi email tampil; data tidak tersimpan. | P2 | N | Belum dijalankan |
| PIM-09 | Hapus karyawan dengan konfirmasi | Karyawan uji sudah ada | 1. Pilih karyawan > **Delete**.<br>2. Klik **Cancel**.<br>3. Ulangi dan klik **Confirm**. | Cancel tidak menghapus data; Confirm menghapus dan karyawan hilang dari list. | P1 | F | Belum dijalankan |
| PIM-10 | Pagination daftar karyawan | Data demo lebih dari satu halaman | 1. Buka Employee List.<br>2. Klik **Next** lalu **Previous**. | Halaman berpindah dengan benar dan data tidak duplikat antar halaman. | P3 | F | Belum dijalankan |

## Leave

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| LVE-01 | Ajukan cuti dengan saldo cukup | Login ESS dengan saldo cuti | 1. Leave > **Apply**.<br>2. Pilih leave type dan rentang tanggal valid.<br>3. Isi alasan, klik Apply. | Toast sukses tampil; request berstatus `Pending`. | P1 | F | Belum dijalankan |
| LVE-02 | Ajukan cuti tanpa leave type | Login ESS | 1. Buka Apply Leave.<br>2. Kosongkan leave type.<br>3. Klik Apply. | `Required` tampil; request tidak terkirim. | P2 | N | Belum dijalankan |
| LVE-03 | Tanggal selesai sebelum tanggal mulai | Login ESS | 1. Isi from `2026-12-10`, to `2026-12-08`.<br>2. Klik Apply. | Pesan validasi tampil; request tidak terkirim. | P2 | N | Belum dijalankan |
| LVE-04 | Cuti beririsan dengan request lain | Sudah ada request Pending | 1. Ajukan cuti dengan tanggal yang beririsan.<br>2. Klik Apply. | Sistem menolak atau memberi peringatan overlap; request tidak terkirim. | P2 | N | Belum dijalankan |
| LVE-05 | Batalkan cuti Pending | Ada request Pending | 1. Buka My Leave.<br>2. Pilih request Pending > **Cancel**. | Status berubah menjadi `Cancelled`. | P2 | F | Belum dijalankan |
| LVE-06 | Setujui cuti sebagai admin | Ada request Pending | 1. Login admin > Leave List.<br>2. Pilih request Pending > **Approve**. | Status menjadi `Approved` dan saldo cuti karyawan berkurang sesuai durasi. | P1 | F | Belum dijalankan |
| LVE-07 | Tolak cuti sebagai admin | Ada request Pending lain | 1. Login admin > Leave List.<br>2. Pilih request > **Reject** dan isi alasan. | Status menjadi `Rejected`; saldo cuti tidak berubah. | P1 | F | Belum dijalankan |
| LVE-08 | Filter Leave List | Ada beberapa request | 1. Buka Leave List.<br>2. Filter status `Pending` dan rentang tanggal.<br>3. Klik Search. | Hanya request yang cocok dengan filter yang tampil. | P2 | F | Belum dijalankan |

## Time

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| TIM-01 | Punch In | Login user dengan akses Time | 1. Time > Attendance > **Punch In**.<br>2. Isi catatan. | Jam masuk tercatat dan status berubah menjadi `Punched In`. | P1 | F | Belum dijalankan |
| TIM-02 | Punch Out | Sudah punch in pada hari yang sama | 1. Klik **Punch Out**.<br>2. Isi catatan. | Jam keluar dan durasi kerja tercatat. | P1 | F | Belum dijalankan |
| TIM-03 | Lihat attendance records | Ada data punch in/out | 1. Time > Attendance > My Records.<br>2. Filter tanggal hari ini. | Record punch in/out tampil sesuai waktu eksekusi. | P2 | F | Belum dijalankan |
| TIM-04 | Submit timesheet | Login user dengan timesheet | 1. Time > Timesheets > My Timesheets.<br>2. Isi jam pada project dan activity.<br>3. Klik Submit. | Timesheet tersimpan dengan status `Submitted`. | P1 | F | Belum dijalankan |
| TIM-05 | Total jam melebihi 24 jam sehari | Timesheet dalam status editable | 1. Isi total jam per hari lebih dari 24.<br>2. Klik Submit. | Pesan validasi tampil; timesheet tidak bisa disubmit. | P2 | N | Belum dijalankan |
| TIM-06 | Setujui timesheet | Ada timesheet `Submitted` | 1. Login approver.<br>2. Timesheets > Approve.<br>3. Pilih timesheet > Approve. | Status timesheet berubah menjadi `Approved`. | P2 | F | Belum dijalankan |

## Recruitment

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| REC-01 | Buat lowongan | Login admin | 1. Recruitment > Vacancies > **Add**.<br>2. Isi vacancy name, job title, hiring manager, jumlah posisi.<br>3. Simpan. | Lowongan muncul di daftar Vacancies. | P1 | F | Belum dijalankan |
| REC-02 | Buat lowongan tanpa field wajib | Login admin | 1. Buka Add Vacancy.<br>2. Kosongkan vacancy name.<br>3. Simpan. | `Required` tampil; lowongan tidak tersimpan. | P1 | N | Belum dijalankan |
| REC-03 | Tambah kandidat dengan resume | Lowongan uji sudah ada | 1. Candidates > **Add**.<br>2. Isi nama, email, unggah PDF kurang dari 1 MB.<br>3. Simpan. | Kandidat muncul dengan status awal `Application Initiated`. | P1 | F | Belum dijalankan |
| REC-04 | Email kandidat tidak valid | Login admin | 1. Add Candidate.<br>2. Isi email `qa-candidate` tanpa domain.<br>3. Simpan. | Pesan validasi email tampil; kandidat tidak tersimpan. | P2 | N | Belum dijalankan |
| REC-05 | Cari dan filter kandidat | Kandidat uji sudah ada | 1. Buka Candidates.<br>2. Cari nama kandidat.<br>3. Filter berdasarkan status. | Hasil sesuai nama dan status yang dipilih. | P2 | F | Belum dijalankan |
| REC-06 | Ubah tahap kandidat | Kandidat status awal | 1. Buka kandidat > **Shortlist**. | Status berubah menjadi `Shortlisted` dan tercatat di riwayat kandidat. | P2 | F | Belum dijalankan |
| REC-07 | Jadwalkan interview | Kandidat sudah shortlisted | 1. Klik **Schedule Interview**.<br>2. Isi interviewer, tanggal, dan waktu.<br>3. Simpan. | Interview tampil dengan status `Scheduled`. | P2 | F | Belum dijalankan |

## My Info

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| MYI-01 | Ubah personal details | Login ESS | 1. My Info > Personal Details.<br>2. Ubah middle name.<br>3. Simpan, lalu reload. | Toast sukses tampil dan perubahan tetap ada setelah reload. | P1 | F | Belum dijalankan |
| MYI-02 | Tambah dependent | Login ESS | 1. My Info > Dependents > **Add**.<br>2. Isi nama dan relationship.<br>3. Simpan. | Dependent muncul di daftar. | P2 | F | Belum dijalankan |
| MYI-03 | Unggah foto profil | Login ESS | 1. Klik foto profil > **Upload**.<br>2. Pilih JPG kurang dari 1 MB.<br>3. Simpan. | Foto baru tampil di halaman My Info. | P3 | F | Belum dijalankan |
| MYI-04 | Employee ID tidak bisa diedit | Login ESS | 1. Buka Personal Details.<br>2. Coba edit field Employee Id. | Field bersifat read-only atau disabled. | P3 | U | Belum dijalankan |
| MYI-05 | Perubahan bertahan setelah reload | MYI-01 sampai MYI-03 selesai | 1. Reload halaman My Info. | Seluruh perubahan sebelumnya masih tersimpan. | P2 | R | Belum dijalankan |

## Admin

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| ADM-01 | Tambah system user | Login admin, ada karyawan uji | 1. Admin > User Management > **Add**.<br>2. Pilih employee, isi username `qa.ess.<tanggal>`, password valid, role ESS.<br>3. Simpan. | User muncul di daftar dengan status `Enabled`. | P1 | F | Belum dijalankan |
| ADM-02 | Username duplikat | User uji sudah ada | 1. Add User.<br>2. Pakai username yang sama.<br>3. Simpan. | Pesan `Already exists` tampil; user tidak tersimpan. | P2 | N | Belum dijalankan |
| ADM-03 | Konfirmasi password tidak cocok | Login admin | 1. Add User.<br>2. Isi password dan confirm berbeda. | Pesan `Passwords do not match` tampil. | P2 | N | Belum dijalankan |
| ADM-04 | Cari dan filter user | User uji sudah ada | 1. Buka User Management.<br>2. Cari username uji.<br>3. Filter role dan status. | Hasil sesuai kriteria; filter bisa dikombinasikan. | P2 | F | Belum dijalankan |
| ADM-05 | Ubah status user | User uji sudah ada | 1. Edit user uji.<br>2. Ubah status `Enabled` menjadi `Disabled`.<br>3. Simpan. | Status berubah dan tersimpan setelah reload. | P2 | F | Belum dijalankan |
| ADM-06 | Hapus user | User uji sudah ada | 1. Pilih user uji > **Delete** > **Confirm**. | User hilang dari daftar. | P3 | F | Belum dijalankan |
| ADM-07 | Job title duplikat | Job title uji sudah ada | 1. Admin > Job > Job Titles > **Add**.<br>2. Isi nama yang sudah ada.<br>3. Simpan. | Pesan duplicate tampil; data tidak tersimpan. | P2 | N | Belum dijalankan |
| ADM-08 | ESS tidak bisa akses menu Admin | User ESS aktif | 1. Login sebagai user ESS.<br>2. Buka `/web/index.php/admin/viewSystemUsers` langsung. | Akses ditolak atau diarahkan; menu Admin tidak tampil. | P1 | N | Belum dijalankan |
| ADM-09 | Tambah lokasi | Login admin | 1. Admin > Organization > Locations > **Add**.<br>2. Isi nama dan country.<br>3. Simpan. | Lokasi baru muncul di daftar. | P3 | F | Belum dijalankan |

## Directory

| ID | Skenario | Prasyarat | Langkah | Hasil diharapkan | P | Jenis | Status |
|---|---|---|---|---|---|---|---|
| DIR-01 | Cari karyawan berdasarkan nama | Karyawan uji punya data directory | 1. Buka Directory.<br>2. Ketik nama karyawan uji. | Kartu karyawan dengan nama, jabatan, dan lokasi tampil. | P1 | F | Belum dijalankan |
| DIR-02 | Filter berdasarkan job title dan location | Karyawan uji punya job title dan lokasi | 1. Pilih job title dan location karyawan uji. | Hasil hanya menampilkan karyawan yang cocok dengan kedua filter. | P2 | F | Belum dijalankan |
| DIR-03 | Pencarian tanpa hasil | — | 1. Cari nama acak yang tidak ada. | Pesan `No Records Found` tampil. | P2 | N | Belum dijalankan |

## Cara mencatat hasil

1. Jalankan kasus sesuai urutan prioritas.
2. Ganti nilai Status menjadi `Pass`, `Fail`, atau `Blocked`.
3. Untuk `Fail`, buat entri di [Bug Reports](03-bug-reports.md) dan tautkan ID-nya.
4. Simpan screenshot di [`evidence/`](../evidence/) dengan nama file yang memuat ID kasus.
5. Setelah sesi selesai, rekap hasil ke [Test Summary Report](05-test-summary-report.md).
