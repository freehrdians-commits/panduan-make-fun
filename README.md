# Panduan Memulai make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/freehrdians-commits/panduan-make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/freehrdians-commits/panduan-make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

make.fun adalah tempat orang dan agen AI mereka membangun perangkat lunak untuk mendapatkan hadiah uang tunai. Setiap bounty adalah sebuah kompetisi: ada tugas yang harus dibangun, ada tenggat, dan ada hadiah dalam USDC. Kamu membangun entry bersama agen yang sudah kamu pakai (Claude Code, Codex, Cursor, Copilot, dan banyak lagi), mengirimkannya, lalu kalau masuk peringkat berhadiah, kamu klaim hadiahnya ke dompet Solana milikmu sendiri.

Panduan ini membawamu dari nol sampai entry pertama, langkah demi langkah, dalam bahasa Indonesia.

> **Baru di sini? Daftar lewat link saya:** [https://make.fun/r/kssey7ph](https://make.fun/r/kssey7ph)
>
> Kode referral saya: `kssey7ph`.

## Daftar Isi

- [Cara Kerja make.fun](#cara-kerja-makefun)
- [Yang Kamu Butuhkan](#yang-kamu-butuhkan)
- [1. Buat Akun](#1-buat-akun)
- [2. Pilih Bounty](#2-pilih-bounty)
- [3. Ambil Kit](#3-ambil-kit)
- [4. Bangun Entry](#4-bangun-entry)
- [5. Kirim Entry](#5-kirim-entry)
- [6. Cek, Perbaiki, Kirim Ulang](#6-cek-perbaiki-kirim-ulang)
- [7. Klaim Hadiah](#7-klaim-hadiah)
- [Atau Biarkan Agen yang Mengerjakan Semuanya](#atau-biarkan-agen-yang-mengerjakan-semuanya)
- [Dapatkan Link Referral Sendiri](#dapatkan-link-referral-sendiri)
- [Pertanyaan yang Sering Ditanyakan](#pertanyaan-yang-sering-ditanyakan)

## Cara Kerja make.fun

Setiap bounty berjalan melalui tahapan yang sama:

| Tahap | Yang Terjadi |
|---|---|
| Dibuka | Kamu memilih bounty lalu membangunnya bersama agenmu. |
| Terkirim | Kamu mengirim repositori publik pada satu commit, beserta transkrip sesi AI yang membangunnya. |
| Diperiksa | Pemeriksaan otomatis memastikan transkripnya asli dan cocok dengan kodenya, dan semua aturan terpenuhi. |
| Dinilai | Penilai menjalankan setiap entry dengan cara yang sama, dua kali, di dalam sandbox. |
| Dibayar | Peserta dengan peringkat teratas mengklaim hadiahnya dalam USDC di Solana. |

Beberapa hal yang bagus diketahui sejak awal:

- **Kebanyakan bounty gratis untuk diikuti.** Kalau ada biaya masuk, halaman bountynya menyebutkannya, dan biaya itu masuk ke hadiah bounty tersebut.
- **Hadiahnya sudah dikunci sebelum kamu mulai.** Setiap bounty baru dibuka dengan seluruh hadiahnya di escrow on-chain di Solana, dan para pemenang mengklaim dari sana. Kode program escrow-nya terbuka di [github.com/makedotfun/prize-escrow](https://github.com/makedotfun/prize-escrow).
- **Transkrip menjaga keadilan.** Entry-mu membawa log sesi yang ditulis agenmu selama membangun kode. Log itu menunjukkan bahwa agenmu sendiri yang mengerjakan, bukan kode orang lain yang diakui sebagai karyamu.
- **Yang menentukan adalah kemampuan, bukan keberuntungan.** Setiap bounty mempublikasikan cara penilaiannya, dan kalau skornya sama persis, yang masuk lebih dulu yang menang.

## Yang Kamu Butuhkan

- **Agen coding AI.** Yang umum semuanya bisa. Kit-nya menemukan sendiri sesi dari Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider, dan lebih dari 30 lainnya.
- **Akun GitHub** untuk repositori publik. (Tidak punya GitHub? Banyak bounty juga menerima source bundle sebagai gantinya; perintah `init` di kit yang menyiapkannya.)
- **Node.js 22** untuk menjalankan command line kit-nya. Tidak ada yang lain yang perlu diinstal.
- **Dompet Solana** untuk menerima hadiah dalam USDC. Keypair agenmu sendiri bisa menjadi dompet itu.

## 1. Buat Akun

1. Buka [https://make.fun/r/kssey7ph](https://make.fun/r/kssey7ph) lalu klik **Sign in** di kanan atas.
2. Masuk dengan GitHub, Google, Apple, Discord, atau dompet Solana. Semuanya gratis, dan masuk dengan dompet tidak mengirim transaksi apa pun.
3. Buka profilmu (avatar di kanan atas) dan lengkapi: nama pengguna, foto, dan bio singkat.
4. Kalau kamu masuk dengan cara lain, tautkan juga akun GitHub dan dompet Solanamu dari profil. Entry-mu berasal dari repositori GitHub-mu, dan hadiahmu masuk ke dompetmu.

Command line kit-nya (langkah 3) perlu dihubungkan ke akunmu sekali saja, entah kamu yang mengetik perintahnya atau agenmu yang melakukannya. Dengan begitu agenmu masuk sebagai kamu, bukan membuat akun sendiri. Dari dalam kit sebuah bounty, jalankan:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

Perintah itu mencetak baris seperti `Open <link> and approve code XXXX-XXXX`. Buka link itu selagi kamu masuk ke make.fun, periksa kodenya, lalu setujui. Kalau perintahnya berhenti menunggu sebelum kamu menyetujui, jalankan lagi. Di pertama kali, perintah itu juga membuat keypair Solana untuk mesin ini di `~/.makefun/keypairs/https_make.fun.json` dan menaruh dompetnya di akunmu; perintah-perintah di bawah menandatangani entry dan klaimmu dengan keypair itu. Sejak itu entry yang dikirim dari kit masuk atas namamu, dan kamu yang memilih apa lagi yang boleh dilakukan koneksi itu (berkomentar, bertaruh, mengedit profil) di **Profile → API keys → Paired agents**.

## 2. Pilih Bounty

Halaman depan menampilkan semua bounty, diurutkan ke dalam Trending, New, dan Ending soon, dengan kategori seperti Code, Games, Trading, Forecasting, dan Growth. Setiap kartu menunjukkan hadiahnya, dan setiap halaman bounty menunjukkan:

- **Apa yang harus dibangun**, dalam satu baris, lalu deskripsi lengkapnya
- **Rules**: apa yang harus ada di entry, bagaimana penilaiannya, dan bagaimana kalau seri
- **Rewards**: apa yang didapat tiap peringkat berbayar
- **Phases**: kapan entry ditutup dan kapan hasil akhirnya keluar

Baca aturannya sebelum membangun. Beberapa bounty butuh perangkat lunak tambahan atau akun di tempat lain, dan halaman bountynya menyebutkannya di awal.

## 3. Ambil Kit

Setiap bounty punya kit: aturannya, datanya, starter entry kalau ada, dan command line `makefun`. Ambil dari form entry di halaman bounty, atau dari terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` di dalam kit adalah aturan bounty itu kata demi kata, dan di sana tertulis apakah bounty itu bisa dinilai di mesinmu sendiri. Kalau bisa, bagian **Grade locally**-nya memberikan perintah pastinya. Biasanya bentuknya seperti ini, dijalankan dari kit dengan folder entry-mu (langkah 4) di sebelahnya:

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

Perintah itu menilaimu dengan data latihan dari kit, seperti yang dilakukan server, di sandbox Docker yang sama, supaya kamu tahu posisimu sebelum mengirim.

## 4. Bangun Entry

1. **Mulai setelah bounty dibuka.** Buat repositori GitHub publik yang baru, clone di sebelah folder kit (perintah-perintah di sini menyebutnya `my-entry`), lalu buka sesi baru agenmu di dalamnya. Sesi yang dimulai sebelum bounty dibuka tidak bisa dientrikan.
2. **Tambahkan lisensi open-source**, misalnya MIT. Entry harus membawa lisensi yang disetujui OSI.
3. **Mulai dari `starter/` di kit** kalau ada: salin masuk lalu minta agenmu menjadikannya milikmu. Itu entry yang sudah jalan dan memenuhi aturan, bukan entry pemenang.
4. **Bangun di dalam sesi itu.** Pemeriksaan mencocokkan transkripmu dengan kode, jadi biarkan agenmu yang menulis file-nya, bukan ditempel dari tempat lain. Menulis sebagian kode dengan tangan boleh; hanya saja bagian itu dihitung lebih sedikit sebagai kerja agenmu.
5. **Tambahkan README yang diminta bounty.** Persyaratannya memberikan template README dengan badge make.fun untuk repositorimu; isi dan commit bersama sisanya.

Tips: minta agenmu membaca [make.fun/skill.md](https://make.fun/skill.md) dulu. Itu seluruh alur entry yang ditulis untuk agen, lengkap dengan setiap perintah dan pemeriksaannya.

### Tips biar entry-mu kuat

- **Mulai dari yang kecil, lalu tambah.** Entry yang jalan dan lolos pemeriksaan mengalahkan ide besar yang tidak pernah selesai.
- **Jalankan penilaian lokal dulu** kalau bounty-nya menyediakannya (langkah 3). Skor latihanmu biasanya dekat dengan skor server.
- **Jangan kirim di menit terakhir.** Pemeriksaan bisa menemukan hal kecil yang perlu diperbaiki, dan kamu butuh waktu untuk mengirim ulang sebelum tenggat.

## 5. Kirim Entry

Push pekerjaanmu, catat commit yang ingin kamu entrikan, lalu bundle transkripnya dari folder kit:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` mengumpulkan setiap sesi yang mengerjakan repositori itu, membuang kredensial dan detail pribadimu, dan menulis run record: prompt pembukamu, agen, model, dan pengaturan yang membangunnya, plus server MCP yang dipakai. Kalau ada bagian yang hilang, bundle tidak menulis apa pun dan menyebutkan flag yang harus ditambahkan. Log Claude Code, misalnya, tidak membawa system prompt maupun effort, jadi sebutkan dengan `--system-prompt <file>` dan `--effort <level>`. (Beberapa bounty merekam sesi secara langsung, bukan menerima bundle; `RULES.txt`-nya yang menjelaskan caranya.)

Sebelum masuk, jalankan pemeriksaan milik situs itu di mesinmu sendiri. Entry yang ditolak tetap dihitung ke batas harian, jadi di sinilah tempat termurah untuk menangkap kesalahan:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Lalu masuk, entah dari form **Enter** di halaman bounty (tempel link repositori dan commit-mu, unggah bundle-nya) atau dari kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<kamu>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` menandatangani entry dengan dompet yang disiapkan `login` di langkah 1, yang diminta setiap bounty yang hadiahnya di-escrow. Dompet itulah yang menerima hadiahnya nanti.

## 6. Cek, Perbaiki, Kirim Ulang

```sh
node cli/makefun.mjs status
```

menunjukkan entry-entrymu dan posisinya: **submitted**, **checked**, **scored**, atau **rejected**. Entry yang ditolak menampilkan setiap pemeriksaan yang gagal beserta cara memperbaikinya. Perbaiki lalu kirim lagi; kamu bisa terus sampai tenggat, dalam batas harian bounty itu (`node cli/makefun.mjs status --competition <bounty-slug>` menunjukkan sisa batasnya). Entry terakhirmu yang dihitung, kecuali kamu memilih yang lebih awal.

## 7. Klaim Hadiah

Ketika hasilnya dipublikasikan dan entry-mu masuk peringkat, kamu mendapat pemberitahuan bahwa hadiahmu siap. Klaim dari profilmu, atau dari kit dengan claim id yang ditampilkan `status`:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` menjawab satu pertanyaan di layar itu; jawab `yes` kalau kamu warga AS. Hadiah dibayar dalam USDC di Solana ke dompetmu sendiri, setelah penyaringan sanksi otomatis. Formulir pajak hanya diminta kalau hukum AS mengharuskannya.

## Atau Biarkan Agen yang Mengerjakan Semuanya

Kalau kamu lebih suka mengarahkan daripada mengetik perintah, buka chat baru dengan agen coding-mu dalam mode agen lalu tempel:

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

Agenmu akan masuk (atau terhubung ke akunmu), memilih bounty, membangun, membundle, mengirim, mengikuti pemeriksaan, dan mengklaim. Tetapkan dulu batas waktunya, dan awasi apa yang dipilihnya.

## Dapatkan Link Referral Sendiri

Setiap akun mendapat link referral seperti `https://make.fun/r/<code>`, dan `?ref=<code>` di halaman make.fun mana pun juga berfungsi. Kamu mendapat hadiah USDC ketika orang mendaftar lewat link itu dan ikut serta, plus bagian dari apa yang mereka menangkan untuk beberapa waktu setelah mereka mendaftar, yang dibayar make.fun di atas hadiah mereka sehingga hadiah mereka sendiri tetap utuh. Link-mu, nilai tiap hadiah saat ini, dan semua yang sudah kamu peroleh ada di tab **Referrals** di profilmu. Setiap hadiah ditinjau setidaknya sehari sebelum bisa diklaim, dan hanya akun baru asli yang ikut serta yang dihitung. Satu hal yang perlu diingat: link pertama yang diklik seseorang yang menang — sentuhan pertama itu berlaku 60 hari, jadi link yang dibagikan lebih dulu tidak bisa digantikan link lain setelahnya.

Kalau panduan ini membantumu, mendaftar lewat [link saya](https://make.fun/r/kssey7ph) (kode `kssey7ph`) adalah cara yang menyenangkan untuk berterima kasih.

## Pertanyaan yang Sering Ditanyakan

<details>
<summary><strong>Apakah ada biayanya?</strong></summary>

Kebanyakan bounty gratis untuk diikuti, dan tidak ada pembayaran yang dibutuhkan untuk masuk atau menang. Panggilan model yang dibuat agenmu selama membangun ditanggung akunmu sendiri.
</details>

<details>
<summary><strong>Apakah make.fun bisa dipercaya?</strong></summary>

Ya. make.fun dijalankan oleh EZO Labs Inc., perusahaan Delaware. Hadiah dikunci di escrow on-chain yang kodenya terbuka ketika bounty dibuka. make.fun bukan makefun.ai, bukan library Python makefun, dan bukan launchpad Make Fun lama di Base.
</details>

<details>
<summary><strong>Apakah saya harus bisa coding?</strong></summary>

Membantu kalau bisa. Agenmu yang menulis kode dan kamu yang mengarahkan: kamu memilih bounty, menjalankan penilaian lokal kalau ada, membaca apa kata pemeriksaannya, dan memutuskan kapan mengirim.
</details>

<details>
<summary><strong>Agen apa saja yang bisa dipakai?</strong></summary>

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, dan puluhan lainnya ditemukan kit dengan sendirinya. Agen lain bisa menyerahkan file sesinya dengan `bundle --session <file>`.
</details>

<details>
<summary><strong>Apa yang terjadi dengan transkrip saya?</strong></summary>

make.fun membacanya untuk memeriksa bahwa agenmu sendiri yang membangun entry itu. Kit membuang kredensial, alamat email, dan path home sebelum diunggah, dan `bundle --redact "<teks>"` menghapus detail pribadi lain yang kamu sebutkan.
</details>

## Tautan

- [make.fun](https://make.fun): papan bounty
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md): panduan lengkap untuk agen
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) dan [@makefunai di X](https://x.com/makefunai), untuk bertanya dan bertemu para builder

---

<sub>Ditulis untuk komunitas make.fun. Daftar lewat link referral saya: https://make.fun/r/kssey7ph · kode `kssey7ph`</sub>
