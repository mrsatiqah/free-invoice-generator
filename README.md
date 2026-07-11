# free-invoice-generator

# Invoice Generator — Log Perubahan

Fail log ini merekod semua perubahan dan penambahan utama yang dibuat untuk **Invoice Generator** (`invoice-generator.html`) dan page panduan yang berkaitan (`panduan-invoice-generator.html`), sejak versi pertama dibina.

---

## 1. Versi Asal — Bina Invoice Generator

- Dibina sebagai satu fail HTML mandiri (single-file), boleh guna terus dari pelayar tanpa install apa-apa.
- Tema warna: navy `#25313C`, sage `#7FA8A5`, cream `#FBEBDA` / `#F6D9B4`, orange `#E2622C` — sepadan dengan design system invois sedia ada.
- Font: **Plus Jakarta Sans** (tajuk), **DM Sans** (body), **Fira Code** (nombor/harga).
- Ciri asal:
  - Muat naik logo perniagaan
  - Maklumat Daripada (Sender) / Kepada (Penerima) — semua field boleh diedit terus
  - No. Invois, Tarikh, Tarikh Akhir
  - Jadual produk/servis dengan kuantiti, harga seunit, jumlah — dikira automatik
  - Subtotal, Diskaun, Cukai/SST(%), Jumlah Perlu Bayar
  - Maklumat Pembayaran (bank, no. akaun, nama akaun) + nota tambahan
  - Ruang tandatangan (lukis atau upload gambar)
  - Butang **Print / Save as PDF**
  - Data kekal dalam pelayar sahaja, tiada disimpan ke server

---

## 2. Kemas Kini Reka Bentuk & Struktur

- **Buang logo** (permintaan awal) — kemudian **letak balik** dengan panduan saiz disyorkan (400×200px, nisbah 2:1, PNG latar lutsinar) supaya logo sentiasa nampak kemas (`object-fit: contain`).
- **Buang border kiri berwarna** pada kotak Daripada/Kepada.
- **Ringkaskan label**: "Daripada (Sender)" → **"Daripada"**, "Kepada (Penerima)" → **"Kepada"**.
- **Buang ruangan tandatangan** sepenuhnya (canvas lukis + upload) untuk jadikan invois lebih *compact* dan muat dalam satu muka surat print.
- **Tukar tajuk lajur** "Perihal Produk / Servis" → **"Produk/Servis"**.
- **Buang ikon 🧾** daripada tajuk "Invoice Generator" di toolbar.
- **Buang ruangan QR / e-Wallet** daripada Maklumat Pembayaran.
- **Sembunyikan kotak Nota Tambahan secara automatik dalam PDF** jika dibiarkan kosong (guna CSS `:placeholder-shown`).
- **Sembunyikan hint "+ Muat naik logo"** semasa print/PDF jika tiada logo diupload — ruang kekal kosong, bukan terpapar teks arahan.

---

## 3. Mobile-Friendly Improvements

- Bersihkan CSS mati (sisa dari ruangan tandatangan yang dah dibuang).
- Elak **auto-zoom iOS Safari** — semua input/textarea minimum saiz font 16px pada skrin kecil.
- Kotak **Jumlah Perlu Bayar** jadi lebar penuh (100%) pada mobile supaya tak overflow.
- Header (logo + tajuk INVOICE) center-align dan stack lebih kemas pada skrin kecil.
- Toolbar (Reset / Tambah Item / Print) stack menegak, sama lebar, senang tap pada telefon.
- **Lajur Kuantiti dikekalkan** pada paparan mobile (asalnya tersorok) — semua 4 lajur jadual (Produk, Kuantiti, Harga, Jumlah) dikecilkan supaya muat dalam satu skrin telefon tanpa perlu sorok maklumat.

---

## 4. Meta Tags & SEO

- Tambah `<title>`, `meta description`, `meta keywords`, `canonical URL`.
- Tambah **Open Graph** (`og:title`, `og:description`, `og:url`, `og:site_name`) dan **Twitter Card** tags untuk paparan lebih menarik bila di-share di media sosial.

---

## 5. Navigasi & Perkongsian

- Tambah link **"← mrsatiqah.github.io"** (home) di toolbar — dikecualikan daripada print/PDF secara automatik (sebab toolbar `display:none` semasa print).
- Tambah **butang share**: Facebook, Twitter/X, Threads, Emel — setiap satu buka link/app dengan caption siap sedia.
- Tambah link **📖 Panduan** ke page panduan berasingan.

---

## 6. Fungsi "Jana sebagai Resit"

- Tambah butang **"🧾 Jana sebagai Resit"** — toggle antara mod Invois dan Resit tanpa perlu isi data dua kali.
- Bila mod Resit diaktifkan:
  - Tajuk "INVOICE" disembunyikan (elak bertindih dengan ribbon)
  - "No. Invois" → **"No. Resit"**
  - "Jumlah Perlu Bayar" → **"Jumlah Dibayar"**
  - Kotak **Maklumat Pembayaran disembunyikan** (sebab dah dibayar)
  - Ribbon banner **"RECEIPT / PAID"** dipaparkan di penjuru kanan atas (reka bentuk diagonal, tergunting kemas di tepi kertas)
- Boleh toggle balik ke mod Invois bila-bila masa — semua data kekal.

---

## 7. Page Panduan Berasingan (`panduan-invoice-generator.html`)

- Dibina dengan tema warna & font yang sama seperti generator utama.
- Kandungan:
  - Gambar rajah invois berlabel nombor (1–6) menunjuk terus ke bahagian yang boleh diedit
  - Langkah demi langkah guna generator (6 langkah)
  - Soalan Lazim (data disimpan ke tak, cara save PDF, guna kat telefon, cara reset)
  - Link balik ke home & butang "Buka Invoice Generator" (atas & bawah)

---

## 8. Tracking / Analytics (GoatCounter)

- Tambah script **GoatCounter** (`mrsatiqah.goatcounter.com`) pada kedua-dua fail untuk track page view.
- Tambah **event tracking** untuk butang-butang penting:
  - `click-print-pdf` — tekan Print/Save PDF
  - `click-mode-receipt` / `click-mode-invoice` — toggle Resit ↔ Invois
  - `click-add-item` — tambah item/baris produk
  - `click-delete-row` — padam baris
  - `click-reset` — tekan Reset
  - `upload-logo` — upload logo
  - `click-home-link` — klik ke laman utama
  - `click-guide-link` — klik ke page panduan
  - `share-facebook`, `share-twitter`, `share-threads`, `share-email` — setiap butang share
  - `click-cta-top`, `click-cta-bottom` — butang CTA pada page panduan

---

## Fail Dalam Projek Ini

| Fail | Fungsi |
|---|---|
| `invoice-generator.html` | Tool utama — jana invois/resit, print/save PDF |
| `panduan-invoice-generator.html` | Page panduan cara guna generator |

---

*Log ini akan dikemas kini setiap kali ada perubahan/penambahan baru pada tool ini.*
