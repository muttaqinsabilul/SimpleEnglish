---
name: bahasa-sederhana
description: |
  Tulis atau tulis ulang teks dalam Bahasa Indonesia yang sederhana dan
  mudah dipahami orang awam, dengan semangat ASD-STE100 Simplified
  Technical English: kalimat pendek, kalimat aktif, satu kata satu makna,
  syarat sebelum perintah, setiap istilah teknis dijelaskan saat pertama
  dipakai, tanpa kata hiasan khas AI. Gunakan untuk dokumentasi, README,
  runbook, prosedur, pesan error, catatan rilis, laporan insiden, panduan
  API, dan penjelasan untuk pembaca di luar bidangnya. Juga gunakan saat
  pengguna menyebut "bahasa sederhana", "bahasa awam", "bahasa yang mudah
  dipahami", "tanpa jargon", "rapikan tulisan ini", "biar gampang dibaca",
  atau meminta teks Bahasa Indonesia yang jelas. Aturan yang sama berlaku
  untuk balasan chat: jawaban dulu, prosa saja.
license: MIT
compatibility: claude-code cursor codex gemini-cli opencode
metadata:
  version: "0.1.0"
  standard: ASD-STE100 Issue 9 (2025-01-15), diadaptasi ke Bahasa Indonesia
---

# Bahasa Sederhana

Tulis Bahasa Indonesia yang sederhana, yang dipahami pembaca cerdas di luar bidangmu dalam sekali baca. Aturannya diadaptasi dari ASD-STE100, bahasa terkontrol untuk manual perawatan pesawat. Ada dua ragam: dokumen yang kamu tulis atau tulis ulang, dan balasan yang kamu ketik di chat. Masing-masing punya aturan pendek di bawah.

## Dokumen

Saat diminta menulis atau menulis ulang dokumentasi, terapkan aturan ini pada prosanya:

1. Kelompokkan setiap bagian. Teks prosedur menyuruh pembaca melakukan sesuatu: kalimat perintah, paling banyak 20 kata, satu instruksi per kalimat. Teks deskripsi menjelaskan: paling banyak 25 kata per kalimat, satu topik per paragraf, paling banyak enam kalimat per paragraf.
2. Jangan ubah kode, identifier, perintah, flag, path file, kutipan error, nama produk, atau fakta. Jika sumber tidak memberi angka atau penyebab, pertahankan pernyataan umumnya.
3. Syarat sebelum perintah, dengan koma: "Jika build gagal, baca log-nya."
4. Pakai kalimat aktif dan sebut pelakunya: "Kamu menjalankan migrasi", bukan "Migrasi dijalankan". Pakai pasif (di-) hanya jika pelakunya memang tidak penting atau tidak diketahui.
5. Kata modal: "harus", "dapat", "akan". Jangan pakai "sebaiknya", "mungkin", "bisa jadi", "seharusnya", "barangkali". "Sebaiknya" yang wajib menjadi "harus". Yang tidak wajib dihapus.
6. Pakai ragam baku yang wajar, ikuti EYD V dan KBBI. Jangan pakai kata gaul atau singkatan chat (yg, dgn, gak, udah) di dokumen. Jangan menulis gaya telegram: pertahankan "yang", "untuk", "dan".
7. Jangan pakai titik koma dan em-dash. Tulis dua kalimat, atau sebut hubungannya ("karena", "tetapi", "misalnya").
8. Satu kata, satu makna, untuk seluruh dokumen. Pakai "pastikan" untuk cek, periksa, verifikasi, validasi, konfirmasi. Pakai "konfigurasi" untuk config, setelan, pengaturan, opsi. Pilih satu bentuk untuk istilah serapan dan pertahankan: jangan bergantian antara "server" dan "peladen".
9. Pecah rangkaian kata benda yang lebih dari tiga kata. "Nilai batas waktu koneksi pool database" menjadi "nilai batas waktu untuk koneksi ke database".
10. Beri pembaca setiap istilah dan fakta sebelum langkah yang membutuhkannya. Jelaskan istilah konsep saat pertama dipakai, kurang dari sepuluh kata. Jangan jelaskan nama produk, nama standar (Postgres, S3, HTTP), atau alat yang dibahas dokumen. Sebut juga host, flag, atau langkah sebelumnya yang dibutuhkan perintah. "Restart service-nya" menjadi "Restart service `sync` di host yang menjalankan job."
11. Nyatakan faktanya, bukan pentingnya. Hapus kata yang tidak membawa fakta: "secara mulus", "dengan mudah", "tangguh", "canggih", "komprehensif", "sangat krusial", "perlu dicatat bahwa", "dalam rangka". Jangan pakai "bukan hanya X, tetapi juga Y". Jangan pakai tiga kata sifat berderet sebagai hiasan. Jangan pakai "kesimpulannya".
12. Pakai format hanya jika membawa struktur. Tanpa label tebal di awal paragraf, tanpa tebal untuk penekanan, tanpa emoji, tanpa judul untuk bagian yang kurang dari tiga kalimat. Daftar vertikal untuk tiga butir sejajar atau lebih: titik dua di kalimat pengantar, huruf kapital di awal butir, satu instruksi per butir.
13. Peringatan: perintah atau syarat dulu, lalu risikonya. "Jangan jalankan perintah ini di production. Perintah ini menghapus baris data."

`references/padanan-kata.md` memetakan kata yang terlalu sering dipakai ke kata yang sederhana.

Sebelum (keluaran AI):

> **Timeout koneksi.** Jika sqlpipe hang atau gagal dengan `dial tcp: i/o timeout`, sebaiknya Anda memverifikasi bahwa host yang menjalankan sqlpipe dapat menjangkau port Postgres (biasanya 5432) — hal ini sering kali disebabkan oleh security group atau firewall yang memblokir koneksi.

Sesudah (prosedur, berjudul, bernomor):

> ## Timeout koneksi
>
> sqlpipe berhenti dengan `dial tcp: i/o timeout` jika tidak dapat terhubung ke port Postgres (default 5432).
>
> 1. Pastikan host yang menjalankan sqlpipe dapat terhubung ke port Postgres. Biasanya firewall atau security group yang memblokirnya.
> 2. Jika database-nya dikelola (RDS, Cloud SQL), pastikan instance-nya menerima koneksi dari IP sqlpipe.

## Balasan

Setiap balasan chat mengikuti aturan ini:

1. Jawab dalam prosa. Tanpa judul, tanpa daftar butir, tanpa tebal, tanpa tabel. Blok kode boleh jika pembaca harus menyalinnya.
2. Kalimat pertama memberi jawaban atau hasilnya. Jangan mengulang pertanyaan.
3. Tanpa em-dash. Sebut hubungannya atau tulis dua kalimat.
4. Jelaskan istilah konsep dengan beberapa kata saat pertama dipakai: "idempoten (aman dijalankan dua kali)". Jangan jelaskan nama produk.
5. Tanpa pembuka ("Tentu saja!", "Pertanyaan yang bagus!") dan tanpa penutup ("Semoga membantu!", "Jangan ragu untuk bertanya").
6. Ikuti tingkat keformalan pengguna. Jika pengguna menulis santai, balas santai tetapi tetap jelas. Jangan memendekkan kutipan error, peringatan keamanan, atau konfirmasi sebelum tindakan yang merusak.

Sebelum: Kegagalan ini berasal dari leader election control-plane saat terjadi pod churn — tidak perlu khawatir!
Sesudah: Pod-nya restart dan antrean kehilangan leader-nya sebentar. Antrean pulih sendiri. Kamu tidak perlu melakukan apa pun.

## Cek Sebelum Menyerahkan

1. Balasan: cari `—`, `**`, `#`, dan baris yang diawali `-`. Hapus setiap temuan.
2. Dokumen: hitung kata di tiga kalimat terpanjang. Jika lebih dari 20 atau 25, pecah. Cari `sebaiknya`, `mungkin`, `seharusnya`, `;`, `—`, `**`, `periksa`, `verifikasi`, `setelan`, dan judul untuk bagian yang kurang dari tiga kalimat. Perbaiki setiap temuan. Baca setiap langkah: apakah langkah itu menyebut host, flag, atau langkah sebelumnya yang harus sudah ada? Jika tidak, tambahkan atau rujuk.

## Batasan

Aturan ini untuk fakta dan instruksi, bukan untuk teks pemasaran atau brand, karena aturan ini menghapus kalimat persuasif. Katakan hal itu, lalu tawarkan aturan ini untuk dokumentasinya.

Skill ini tidak punya mode Strict. ASD-STE100 hanya punya kamus bahasa Inggris. Untuk teks bahasa Inggris, pakai skill `simple-english`.

## Referensi

- `references/padanan-kata.md`: peta dari kata yang terlalu sering dipakai ke kata yang sederhana
