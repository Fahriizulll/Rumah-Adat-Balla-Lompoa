# Tur Virtual Rumah Adat Baruga

Tur virtual 360 derajat untuk mengenalkan Rumah Adat Baruga sebagai balai adat komunal. Proyek ini berfokus pada pengalaman interaktif melalui rangkaian panorama equirectangular, dilengkapi landing page informatif, dua varian tampilan tur, serta panel admin ringan untuk mengelola daftar scene.

## Fitur Utama

- Landing page tematik (`index.html`) dengan deskripsi arsitektur Baruga dan tombol ajakan (CTA) menuju tur.
- Tur utama (`baruga.html`) berbasis Pannellum dengan 54 titik (0-53), tombol minimap, toggle drag, dan overlay koordinat yaw/pitch.
- Tur lanjutan (`baruga_adv.html`) menambahkan navigasi grid, highlight scene aktif, kontrol prev/next, shortcut keyboard, serta hotspot otomatis antar scene.
- Panel admin (`admin.html`) untuk CRUD data scene, pratinjau gambar, impor/ekspor JSON, dan generator `tour.html`. Data disimpan di localStorage.
- Struktur aset terorganisir: folder `panos/` untuk panorama, `images/` untuk hero dan minimap, serta stylesheet terpisah.

## Struktur Proyek

```text
.
├── index.html          # Landing page tur virtual
├── baruga.html         # Tur utama dengan tombol scene statis
├── baruga_adv.html     # Tur lanjutan dengan navigasi dinamis dan hotspot
├── admin.html          # Panel pengelolaan scene (client-side)
├── css/
│   └── homestyle.css   # (opsional) ruang untuk gaya tambahan
├── images/
│   ├── main_img.jpg    # Hero landing page
│   └── minimap.jpg     # Minimap modal di baruga.html
├── panos/
│   └── image0.jpg ... image53.jpg  # Panorama equirectangular
├── README.md
└── TODO.txt            # Ruang pencatatan pengembangan berikutnya
```

## Menjalankan Secara Lokal

1. Unduh atau clone repositori ini.
2. Jalankan server statis, misalnya `python3 -m http.server 8000`.
3. Buka `http://localhost:8000/index.html` di peramban modern (Chrome, Firefox, Edge).
4. Pastikan seluruh berkas panorama berada di `panos/` agar Pannellum dapat memuatnya tanpa kendala CORS.

Alternatif cepat: gunakan ekstensi Live Server (VS Code) atau layanan hosting statis (Netlify, Vercel, GitHub Pages).

## Panduan Penggunaan

- Landing Page (`index.html`)
  - Menampilkan ringkasan Baruga, foto hero, dan tombol masuk ke tur virtual.
- Tur Utama (`baruga.html`)
  - Tombol 0-53 memuat scene secara langsung.
  - Tombol "Tampilkan Minimap" membuka peta lokasi panorama.
  - Tombol "Nonaktifkan Drag" mengubah mode klik menjadi pembaca koordinat yaw/pitch.
- Tur Lanjutan (`baruga_adv.html`)
  - Grid tombol mempermudah lompatan lintas scene.
  - Tombol Prev/Next serta tombol panah keyboard mengatur urutan kunjungan.
  - Hotspot otomatis pada panorama menghubungkan scene sebelumnya dan berikutnya.

## Panel Admin (`admin.html`)

1. Isi form scene (index, judul, nama file, yaw/pitch/hfov, tautan hotspot).
2. Tekan **Simpan / Update** untuk menambah atau memperbarui entri; data tersimpan ke localStorage dengan key `barugaScenes`.
3. Gunakan **Import JSON** atau **Export JSON** untuk memindahkan konfigurasi antar perangkat.
4. Pilih **Export tour.html** untuk menghasilkan berkas HTML siap pakai berbasis konfigurasi saat ini.
5. Fitur pratinjau mendukung drag and drop; file panorama asli tetap harus ditempatkan manual di folder `panos/`.

## Manajemen Panorama

- Gunakan penamaan konsisten `image{index}.jpg` atau sesuaikan script sesuai pola file.
- Format panorama: equirectangular 2:1 (misal 6000x3000 piksel) agar tampilan maksimal.
- Kompresi gambar (JPEG kualitas 80-90) untuk menjaga performa pemuatan.
- Untuk mengubah titik awal (yaw/pitch/hfov), perbarui input di panel admin atau langsung pada konfigurasi `baruga_adv.html`.

## Kustomisasi

- Ubah skema warna via variabel CSS di masing-masing file HTML.
- Tambah konten budaya atau informasi sejarah langsung pada landing page.
- Modifikasi objek `overrides` di `baruga_adv.html` jika ingin menentukan default yaw/pitch berbeda per scene.
- Tambahkan hotspot tematik (info, link, video) dengan mengikuti format `hotSpots` Pannellum.

## TODO atau Pengembangan Lanjutan

Catat ide lanjutan di `TODO.txt`, misalnya:
- Narasi audio atau teks multilanguage.
- Integrasi menu kategori scene (serambi, halaman tengah, sayap bangunan).
- Otomasi kompresi panorama sebelum deploy.

## Lisensi

Tambahkan keterangan lisensi sesuai kebutuhan proyek (misal hak cipta institusi, Creative Commons, dan lain-lain).
