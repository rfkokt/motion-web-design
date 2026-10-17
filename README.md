# Web Motion Design

Skill portabel untuk merancang, membuat, dan menguji motion website. Mencakup scroll storytelling, kinetic typography, SVG path, horizontal pinning, media reveal, dan physics saat memang dibutuhkan.

## Install di Kern Studio

1. Buka panel **Skills**, lalu **Install Skill**.
2. Pilih tab **Git Repository**.
3. Isi **Repository URL or owner/repository** dengan `rfkokt/motion-web-design` atau `https://github.com/rfkokt/motion-web-design.git`.
4. Biarkan **Branch, tag, or commit** dan **Skill path inside repository** kosong. Skill tersedia di root branch default (`main`).
5. Klik **Preview & validate**, lalu pilih `motion-web-design`.
6. Klik **Install selected**.

Installer Kern Studio menyalin skill beserta file pendukung ke `~/.pi/agent/skills/motion-web-design`. Metadata `agents/openai.yaml` bersifat opsional untuk Codex; inti skill memakai Markdown dengan YAML frontmatter dan tidak bergantung pada Codex atau MCP tertentu.

Repo ini public. Kern Studio dapat melakukan clone melalui HTTPS tanpa login GitHub.

## Pemakaian

Minta agent menggunakan skill yang sudah dipasang, misalnya:

> Gunakan skill motion-web-design untuk membuat portfolio dengan satu scene SVG mengikuti scroll dan layout mobile yang sederhana.

> Gunakan skill motion-web-design untuk audit animasi halaman ini, terutama resize, keyboard, dan reduced motion.

Untuk Codex, bisa dipanggil dengan `$motion-web-design`.

Skill menyesuaikan stack dan tujuan website. CSS cukup untuk efek sederhana; timeline, SVG, Lottie, video, canvas/physics, atau WebGL dipilih sesuai kebutuhan. Tidak ada library runtime yang harus dipasang hanya untuk menggunakan skill ini.

## Isi repository

```text
SKILL.md                         Instruksi utama dan kondisi pemakaian
agents/openai.yaml               Metadata opsional untuk Codex
references/motion-patterns.md    Pilihan teknik, geometri, lifecycle
references/verification.md       Skenario QA dan standar bukti
references/reference-study.md    Pelajaran dari studi Motion Zajno
```

Materi studi merujuk pada pengamatan Oktober 2026, bukan jaminan tentang implementasi terbaru situs referensi. Paket ini berisi panduan; tidak membawa kode, media, branding, atau font milik situs referensi.

## Memperbarui skill

Jalankan kembali **Preview & validate** dari repo yang sama. Untuk mengganti versi yang sudah terpasang, pilih opsi **Replace an existing same-name skill**, lalu **Install selected**. Kern Studio membuat backup sebelum mengganti skill.
