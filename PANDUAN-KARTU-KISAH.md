# Aturan kartu kisah per tokoh

Di website ini, **struktur kartu yang terlihat ditentukan oleh `children` dalam `index.html`**. File HTML di `data/bio/` hanya menyimpan isi kartu. Menaruh file pada folder yang benar tanpa menautkan `children` tidak cukup.

## Menambahkan kisah baru (metode aman)

1. Temukan `infoNote:"@bio:SLUG-TOKOH"` di `index.html`; gunakan slug itu **persis**. Pastikan `data/bio/SLUG-TOKOH.html` ada.
2. Simpan isi kartu kisah dalam HTML UTF-8 terpisah, misalnya `kisah-baru.html`.
3. Dari akar repository, jalankan:

   ```bash
   python tools/tambah_kisah.py --tokoh al-junaid-al-baghdadi --slug nasihat-keikhlasan --judul "NASIHAT TENTANG KEIKHLASAN" --html-file kisah-baru.html --dry-run
   python tools/tambah_kisah.py --tokoh al-junaid-al-baghdadi --slug nasihat-keikhlasan --judul "NASIHAT TENTANG KEIKHLASAN" --html-file kisah-baru.html
   ```

4. Hasilnya ada di `data/bio/al-junaid-al-baghdadi/nasihat-keikhlasan.html`, dan kartu masuk ke `children` milik **Al-Junaid**, bukan sejajar dengan Al-Junaid atau tokoh lain. Fungsi `loadBioFile` sudah mendukung path subfolder.
5. Periksa `git diff` dan uji website lewat server lokal (bukan `file://` karena `fetch` file HTML).

Alat akan **menolak**, tanpa mengubah file, jika slug tokoh tidak unik/tidak ada, biografi induk hilang, isi kisah kosong, atau kartu/file kisah sudah pernah ditambahkan. Jangan menambahkan kisah baru secara manual sebagai saudara tokoh di array kategori.

## Kebijakan untuk AI atau kontributor berikutnya

- Kenali tokoh induk berdasarkan `infoNote` unik sebelum menulis kartu.
- Semua kisah baru harus ditulis ke `data/bio/<slug-tokoh>/` menggunakan alat `tools/tambah_kisah.py`.
- Semua node kisah harus berada dalam `children` tokoh tersebut; jangan masukkan ke `children` kategori atau sejajar dengan tokoh lain.
- Jika nama tokoh/slug ambigu, **jangan menebak** atau mengubah struktur; identifikasi tokoh yang benar lebih dulu.
- Jangan memindahkan file/kartu lama secara massal tanpa memeriksa pemilik kisah dan seluruh tautannya. Struktur lama dipertahankan agar kartu yang sudah berfungsi tidak rusak.
- Mekanisme ini menjaga penambahan kisah **melalui alat tersebut**; edit manual langsung pada `index.html` tetap dapat membuat kesalahan.
