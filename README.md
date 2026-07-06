# Diskusi Kasus Radiologi — RS Mitra Plumbon

Web forum untuk diskusi kasus antar dokter Sp.Rad, realtime via Firebase.

## Isi folder
- `index.html` — aplikasi utama (siap upload ke GitHub Pages)
- `database.rules.json` — rules keamanan Firebase (schema validation)
- `seed-data.json` — contoh struktur data awal (opsional, boleh diimport atau diabaikan)

## Cara pasang RULES di Firebase
1. Buka [Firebase Console](https://console.firebase.google.com/) → project **doublereading-rad**.
2. Masuk ke **Realtime Database** → tab **Rules**.
3. Copy-paste isi `database.rules.json`, lalu **Publish**.

## Cara isi data awal (opsional)
1. Di Realtime Database, klik menu titik tiga (⋮) → **Import JSON**.
2. Pilih file `seed-data.json` — ini hanya contoh 1 kasus + 1 komentar, boleh dilewati jika ingin mulai dari kosong (data `doctors` di sini hanya referensi, aplikasi tidak membacanya karena daftar dokter sudah tertanam di `index.html`).

## Cara upload ke GitHub Pages
1. Buat repository baru, misal `diskusi-radiologi-rad`.
2. Upload `index.html` (dan file lain jika ingin disimpan sebagai dokumentasi) ke repo tersebut.
3. Masuk ke **Settings → Pages** → Source: pilih branch `main`, folder `/root` → Save.
4. Tunggu 1-2 menit, web akan aktif di `https://<username>.github.io/<nama-repo>/`.

## Cara pakai
1. Buka web, pilih nama dokter dari dropdown (tidak perlu password — akses dibatasi karena link hanya dibagikan ke 4 dokter terkait).
2. Klik **Kasus Baru** untuk mengajukan kasus: judul, modalitas, link gambar Google Drive (opsional), dan deskripsi/pertanyaan.
3. Dokter lain bisa membuka kasus dan memberi tanggapan secara realtime di kolom diskusi.
4. Kasus bisa ditandai **Selesai** oleh siapa saja, dan dibuka kembali bila perlu.
5. Hanya pembuat kasus yang bisa menghapus kasusnya.

## Tips link gambar Google Drive
Upload gambar radiologi (screenshot CT/MRI/X-Ray) ke Google Drive → klik kanan → **Share** → set ke "Anyone with the link" → **Copy link** → tempel ke kolom "Link Gambar" saat membuat kasus baru. Aplikasi otomatis mengubahnya ke format yang bisa langsung tampil sebagai gambar.

## Catatan keamanan
Karena tidak memakai Firebase Authentication, keamanan mengandalkan:
- URL web dan URL database tidak disebar ke luar tim.
- Rules Firebase memvalidasi struktur data (schema validation) sehingga data acak/rusak tidak bisa masuk.
- Jika suatu saat perlu login lebih ketat (misal PIN per dokter), ini bisa ditambahkan kemudian.
