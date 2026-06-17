# Usability Timer Tracker

Aplikasi web sederhana (single-file, tanpa backend/database) untuk mencatat
waktu pengerjaan (time on task), jumlah error, dan jumlah klik per task saat
melakukan task-based usability testing. Dirancang untuk dibuka di iPad/tablet
secara terpisah dari device yang sedang diuji.

Data disimpan di `localStorage` browser (tidak terkirim ke server mana pun),
dan bisa diekspor sebagai file CSV kapan saja.

## Cara deploy ke Vercel (gratis)

### Opsi A — lewat website Vercel (tanpa command line)

1. Buat akun gratis di https://vercel.com (bisa daftar pakai akun GitHub/Google/email).
2. Upload folder ini ke GitHub:
   - Buat repository baru di https://github.com/new (boleh public atau private).
   - Upload `index.html`, `vercel.json`, dan `README.md` ke repo tersebut
     (lewat tombol "Add file" → "Upload files" di GitHub, tanpa perlu git command).
3. Di dashboard Vercel, klik **Add New → Project**.
4. Pilih repository GitHub yang baru dibuat tadi, klik **Import**.
5. Biarkan semua setting default (Framework Preset: Other), klik **Deploy**.
6. Setelah selesai (~30 detik), Vercel akan memberi URL publik seperti
   `https://usability-timer-xxxx.vercel.app` — itu yang dibuka di iPad.

### Opsi B — lewat terminal (kalau familiar command line)

```bash
npm install -g vercel
cd usability-timer
vercel
```

Ikuti instruksi login lalu deploy; Vercel CLI akan otomatis memberi URL publik.

## Cara pakai

1. Buka URL Vercel tersebut di Safari/Chrome iPad, lalu opsional: tambahkan ke
   Home Screen (tombol Share → "Add to Home Screen") supaya terasa seperti app.
2. Isi jumlah task (default 6) dan nama/ID responden, tekan **Mulai sesi testing**.
3. Untuk tiap task: tekan **Mulai** saat responden mulai mengerjakan, **Stop**
   saat selesai. Gunakan tombol `+`/`–` pada kartu **Error** dan **Klik** untuk
   mencatat secara real-time.
4. Setelah satu responden selesai semua task, tekan **Selesai responden**.
5. Tekan **Tambah responden baru** untuk lanjut ke orang berikutnya.
6. Setelah semua responden selesai (atau sewaktu-waktu), tekan
   **Export semua data (CSV)** — file CSV otomatis terunduh dan bisa dibuka
   langsung di Excel/Google Sheets.

## Catatan penting

- Data tersimpan secara lokal di browser perangkat tersebut (`localStorage`).
  Jangan membersihkan cache/data browser sebelum sempat export, atau data akan
  hilang.
- Kalau halaman ter-refresh secara tidak sengaja saat sesi sedang berjalan,
  aplikasi otomatis memulihkan sesi responden yang belum selesai (asal cache
  browser belum dibersihkan).
- Karena semuanya berjalan di sisi browser (client-side), tidak perlu koneksi
  internet setelah halaman pertama kali dimuat — cocok untuk lokasi yang
  sinyalnya kurang stabil. Tapi pastikan halaman sempat dimuat penuh sebelum
  offline.
- Tombol **Hapus semua data** akan menghapus seluruh data responden yang
  tersimpan secara permanen — gunakan dengan hati-hati, dan pastikan sudah
  export CSV sebelum menghapus.
