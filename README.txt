CARA MENAMBAH TOKOH BARU (sahabat, tabiin, dll)
================================================
1. Tulis biografinya sebagai potongan HTML (<p>, <h5>, <b>, dst, seperti file lain)
   lalu simpan di:   data/bio/nama-tokoh.html
   (huruf kecil, pakai tanda hubung, tanpa spasi)

2. Di data pohon (index.html), pada tokoh itu tulis:
   infoNote: "@bio:nama-tokoh"

3. Upload ulang folder ke hosting. Selesai.
   Halaman awal tidak bertambah berat, karena isi biografi baru diunduh saat diklik.

CATATAN
- Wajib dibuka lewat hosting/server (https://...), bukan file:// langsung.
- Nama file di data/bio harus sama persis dengan setelah "@bio:".
