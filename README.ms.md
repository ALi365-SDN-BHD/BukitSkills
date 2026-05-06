# Bukit Agent Skills

[English](./README.md) | [简体中文](./README.zh-CN.md)

`BukitSkills` ialah repositori skill khusus Bukit untuk AI Agent. Aset utamanya terletak dalam direktori akar `skills/` sebagai fail `SKILL.md` yang fokus. Repositori ini bukan kod sumber runtime Bukit dan bukan projek tapak yang boleh terus dijalankan. Sebaliknya, ia membantu agent memilih sempadan pengetahuan yang betul apabila bekerja dengan Bukit.

Jika anda menggunakan Bukit melalui Trae, Claude Code, Copilot CLI, Codex CLI, Gemini CLI, atau persekitaran lain yang menyokong skill, anggap repositori ini sebagai lapisan navigasi untuk agent:

- Mulakan dengan `using-bukit` apabila tugasan secara jelas menggunakan Bukit
- Gunakan `bukit-cli-reference` sebagai sumber tunggal untuk pelaksanaan arahan
- Muatkan sub-skill yang sepadan untuk konfigurasi, tema, templating, Notion, routing, i18n, atau plugin/debug

## Skop Projek

- Ini ialah repositori dokumentasi skill, bukan repositori kod runtime
- Repositori ini sendiri tidak mengandungi `package.json`, `site.yaml`, Docker, atau konfigurasi CI
- Ia menghimpunkan pecahan tugasan Bukit, pengetahuan konfigurasi, dan panduan pelaksanaan
- Ia paling sesuai digunakan sebagai pintu masuk, indeks, dan rujukan pantas untuk agent yang mengendalikan tugasan Bukit

## Susun Atur Repositori

```text
BukitSkills/
  README.md
  README.zh-CN.md
  README.ms.md
  skills/
    using-bukit/            # Pintu masuk dan routing bersatu
    bukit-cli-reference/    # Sumber tunggal untuk operasi CLI
    bukit-config/           # Model konfigurasi site.yaml
    bukit-theme/            # Direktori tema, aset, dan parameter
    bukit-templating/       # Pembangunan templat Scriban
    bukit-notion/           # Integrasi sumber kandungan Notion
    bukit-routing/          # Routing URL dan permalink
    bukit-i18n/             # Tapak berbilang bahasa
    bukit-plugins-debug/    # Plugin, incremental build, diagnostik
```

## Gambaran Skill

| Skill | Tanggungjawab | Kegunaan biasa |
|---|---|---|
| `using-bukit` | Skill gerbang Bukit yang mengenal pasti kerja dan menghala ke sub-skill | Pengguna menyebut "using bukit" atau tugasan jelas khusus untuk Bukit |
| `bukit-cli-reference` | Pengesanan CLI, panduan pemasangan, rujukan arahan, output, dan tafsiran exit code | Menjalankan `bukit build`, `init`, `preview`, `doctor`, `theme`, `webhook`, dan arahan berkaitan |
| `bukit-config` | Struktur `site.yaml`, templat senario, dan penerangan medan | Mencipta atau menyunting konfigurasi tapak, menerangkan medan, membaiki ralat validasi |
| `bukit-theme` | Struktur direktori tema, organisasi aset statik, dan parameter tema | Mencipta atau memindahkan tema, membaiki isu CSS atau aset statik |
| `bukit-templating` | Sintaks Scriban, pewarisan layout, dan corak templat | Menulis templat halaman, halaman senarai, pagination, atau membaiki isu render templat |
| `bukit-notion` | Integrasi Notion, pemetaan property, render blok, dan penyetempatan imej | Menggunakan Notion sebagai CMS atau menyelesaikan masalah fetch dan pemetaan |
| `bukit-routing` | Permalink, route collection, pengekodan URL, dan tingkah laku output path | Menyesuaikan URL, membaiki 404, menyelesaikan konflik route, mengkonfigurasi halaman senarai |
| `bukit-i18n` | Pengesanan bahasa, build berasingan mengikut bahasa, dan output gabungan | Membina tapak berbilang bahasa dan menyahpepijat isu pertukaran bahasa atau output gabungan |
| `bukit-plugins-debug` | Kitar hayat plugin, tingkah laku incremental build, diagnostik prestasi, dan troubleshooting | Plugin tidak berjalan, output salah, atau prestasi build merosot |

## Cara Menggunakan Repositori Ini

Turutan pemuatan yang disyorkan:

1. Mulakan dari `using-bukit` sebaik sahaja tugasan disahkan sebagai tugasan Bukit
2. Gunakan `bukit-cli-reference` untuk setiap langkah berkaitan arahan
3. Muatkan `bukit-config` apabila tugasan bergantung pada pengetahuan latar konfigurasi
4. Baca `bukit-theme` sebelum `bukit-templating` apabila kerja templat bergantung pada struktur tema
5. Gunakan `bukit-notion`, `bukit-routing`, `bukit-i18n`, atau `bukit-plugins-debug` mengikut keperluan

Satu aliran kerja biasa kelihatan seperti ini:

```text
using-bukit
  -> bukit-cli-reference
  -> bukit-config
  -> bukit-theme / bukit-notion / bukit-routing / bukit-i18n / bukit-plugins-debug
  -> bukit-templating
```

## Aliran Minimum Bukit

Repositori ini sendiri bukan tapak Bukit. Jangan jalankan `bukit build` atau `bukit preview` dari akar repo ini. Untuk mencuba aliran minimum Bukit, jalankan arahan berikut di dalam direktori tapak Bukit sebenar:

```bash
bukit version
bukit init ./my-site --provider markdown
cd my-site
bukit build
bukit preview
```

Nota:

- `bukit build` dan `bukit preview` mesti dijalankan dalam akar tapak yang mengandungi `site.yaml`
- Direktori output lalai biasanya ialah `dist`
- Tapak berasaskan Notion biasanya memerlukan `NOTION_TOKEN`
- Pada Windows, penggunaan fail boleh laku secara terus biasanya berbentuk `.\bukit.exe version` atau `& .\bukit.exe version`

## Laluan Bacaan Disyorkan

### Cipta tapak baharu

1. `using-bukit`
2. `bukit-cli-reference`
3. `bukit-config`
4. `bukit-theme`
5. `bukit-templating`

### Konfigurasi Notion sebagai sumber kandungan

1. `using-bukit`
2. `bukit-notion`
3. `bukit-config`
4. `bukit-cli-reference`

### Ubah routing dan halaman senarai

1. `using-bukit`
2. `bukit-routing`
3. `bukit-config`
4. `bukit-templating`

### Nyahpepijat isu build atau plugin

1. `using-bukit`
2. `bukit-plugins-debug`
3. `bukit-config`
4. `bukit-cli-reference`

## Nota Penyelenggaraan

- Simpan setiap skill di `skills/<skill-name>/SKILL.md`
- Gunakan `description` hanya untuk syarat pencetus, bukan ringkasan umum
- Pusatkan semua arahan CLI dan nota pelaksanaan dalam `bukit-cli-reference`
- Pastikan laluan tema, medan konfigurasi, dan parameter CLI selari dengan tingkah laku sebenar Bukit
- Apabila Bukit mendapat kemampuan baharu, tentukan sama ada perlu mengembangkan skill sedia ada atau menambah skill baharu dengan sempadan yang jelas

## Dokumen

- English: [`README.md`](./README.md)
- 中文: [`README.zh-CN.md`](./README.zh-CN.md)
- Bahasa Melayu: [`README.ms.md`](./README.ms.md)
- Semua dokumen skill berada dalam [`skills/`](./skills)
