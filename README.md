# Khayal

Plugin skill untuk mengubah imajinasi pengguna menjadi website (dan nanti video) yang tidak terasa buatan AI, dengan satu arah desain yang dipakai bersama. Berjalan di Claude Code dan Antigravity dengan skill yang sama. Isi skill ditulis dalam bahasa Inggris (supaya instruksi ke model akurat), dan skill menjawab dalam bahasa pengguna.

## Skill (4)

- `khayal-guide`: pintu masuk. Menjelaskan apa yang bisa dilakukan Khayal dan mengarahkan ke skill yang tepat.
- `khayal-brief`: menggali ide yang masih kabur menjadi `BRIEF.md`, lalu menawarkan tiga arah desain.
- `khayal-web`: alur utama membangun website 2D, 3D, atau hybrid. Pengguna berimajinasi dulu, lalu memilih jenis web, lalu Claude meriset pemenang Awwwards dan kompetitor, menawarkan tiga arah, dan baru membangun sampai uji di browser. Panduan rincinya ada di `skills/khayal-web/references/`:
  - `web-type.md`: memilih 2D, 3D, atau hybrid, dan aturan 3D (fallback, beban, frame rate)
  - `research.md`: riset Awwwards dan kompetitor, format `REFERENCES.md`
  - `landing-page.md`: langkah tambahan untuk halaman konversi
  - `direction.md`: cara menulis `DESIGN.md`
  - `interaction.md`: interaksi yang punya tujuan, aksesibilitas, daftar uji
  - `copy.md`: copy yang spesifik dan jujur
  - `audit.md` dan `tanda-slop.md`: audit halaman terhadap tanda "AI slop"
  - `template-prompt.md`: template prompt

- `khayal-bench`: benchmark teknik web (CSS+GSAP, SVG, shader, Three.js, CSS 3D, Lottie/Rive/Spline, dan lainnya) dengan tiga tingkat low, mid, high. Pengguna memilih ID yang diuji, Claude membangun dan mengukur di Chrome asli, pengguna yang menilai tampilannya. Katalog ada di `skills/khayal-bench/references/catalog.md`.

Rujukan di bawah `khayal-web` bukan skill terpisah. Belum ada: skill video (rencana: Remotion, memakai warna, font, dan bahasa gerak dari `DESIGN.md`).

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
  skills/khayal-guide/SKILL.md
  skills/khayal-brief/SKILL.md
  skills/khayal-web/SKILL.md
  skills/khayal-web/references/      panduan rinci yang dimuat bila perlu
  skills/khayal-bench/SKILL.md
  skills/khayal-bench/references/    katalog, cara ukur, lembar review
```

## Yang perlu kamu isi sebelum dipublikasikan

- Nama pemilik di `marketplace.json` dan `author` di kedua manifest (sekarang placeholder atau kosong).
- Field `repository` dan lisensi (belum ada file LICENSE).
- Logo, bila ingin masuk marketplace Antigravity.

## Asal isi

Dirangkum dengan kata sendiri dari riset prompt anti slop: Anthropic Cookbook tentang estetika frontend, artikel capitalandcompute tentang tanda slop, artikel prg.sh tentang kenapa AI membuat desain yang sama, dan praktik aksesibilitas gerak. Konsep tiga dial (ENERGY, RHYTHM, MOTION) terinspirasi dari plugin antislop (MIT). Semuanya opini praktisi dan dokumentasi vendor, bukan standar baku.
