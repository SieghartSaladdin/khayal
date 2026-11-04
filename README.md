# Khayal

Plugin skill untuk mengubah imajinasi pengguna menjadi website (dan nanti video) yang tidak terasa buatan AI, dengan satu arah desain yang dipakai bersama. Berjalan di Claude Code dan Antigravity dengan skill yang sama. Isi skill ditulis dalam bahasa Inggris (supaya instruksi ke model akurat), dan skill menjawab dalam bahasa pengguna.

## Skill

- `khayal-brief`: menggali ide yang masih kabur menjadi `BRIEF.md`, lalu menawarkan tiga arah desain.
- `khayal-direction`: menulis `DESIGN.md` (konsep, palet, tipografi, elemen utama, ritme, gerak, larangan) yang dipakai semua keluaran.
- `khayal-web`: alur utama membangun website, plus template prompt di `references/template-prompt.md`.
- `khayal-interaction`: interaksi yang punya tujuan, pilihan stack, aksesibilitas, performa, daftar uji.
- `khayal-audit`: audit halaman terhadap daftar tanda slop (`references/tanda-slop.md`), temuan bernomor.
- `khayal-copy`: copy yang spesifik dan jujur, tanpa angka atau testimoni karangan.

Belum ada: `khayal-video` (rencana: Remotion, memakai warna, font, dan bahasa gerak dari `DESIGN.md`).

## Instal di Claude Code

Coba tanpa menginstal:

```bash
claude --plugin-dir ./khayal
```

Instal lewat marketplace lokal atau repositori Git:

```bash
claude plugin marketplace add ./khayal
claude plugin install khayal@khayal-marketplace
```

Untuk repositori GitHub, ganti `./khayal` dengan `pemilik/nama-repo`.

## Instal di Antigravity

```bash
agy plugin validate --strict ./khayal
agy plugin install ./khayal
agy plugin list
```

Antigravity juga bisa memasang dari tautan repositori GitHub.

## Struktur

```
khayal/
  .claude-plugin/plugin.json         manifest Claude Code
  .claude-plugin/marketplace.json    marketplace Claude Code
  .antigravity-plugin/plugin.json    manifest Antigravity
  skills/<nama>/SKILL.md             skill yang sama untuk keduanya
  skills/<nama>/references/          bahan rujukan yang dimuat bila perlu
```

## Yang perlu kamu isi sebelum dipublikasikan

- Nama pemilik di `marketplace.json` dan `author` di kedua manifest (sekarang placeholder atau kosong).
- Field `repository` dan lisensi (belum ada file LICENSE).
- Logo, bila ingin masuk marketplace Antigravity.

## Asal isi

Dirangkum dengan kata sendiri dari riset prompt anti slop: Anthropic Cookbook tentang estetika frontend, artikel capitalandcompute tentang tanda slop, artikel prg.sh tentang kenapa AI membuat desain yang sama, dan praktik aksesibilitas gerak. Konsep tiga dial (ENERGY, RHYTHM, MOTION) terinspirasi dari plugin antislop (MIT). Semuanya opini praktisi dan dokumentasi vendor, bukan standar baku.
