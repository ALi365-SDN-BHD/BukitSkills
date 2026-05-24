# Bukit Agent Skills

[English](./README.md) | [简体中文](./README.zh-CN.md)

`BukitSkills` ialah repositori skill khusus Bukit untuk AI Agent. Aset utamanya berada dalam direktori akar `skills/`, terdiri daripada fail `SKILL.md` yang fokus serta katalog boleh dibaca mesin. Repositori ini bukan kod sumber runtime Bukit dan bukan projek tapak yang boleh terus dijalankan. Sebaliknya, ia membantu agent memilih sempadan pengetahuan yang betul apabila mencipta, mengkonfigurasi, menyahpepijat, mengoptimumkan, mempratonton, mendeploy, atau mengklon tapak Bukit.

Jika anda menggunakan Bukit melalui Trae, Claude Code, Copilot CLI, Codex CLI, Gemini CLI, atau persekitaran lain yang menyokong skill, anggap repositori ini sebagai lapisan navigasi untuk agent:

- Mulakan dengan `using-bukit` apabila tugasan secara jelas menggunakan Bukit atau Bukit patut menjadi penjana laman statik
- Gunakan `bukit-cli-reference` sebagai sumber tunggal sebelum melaksanakan sebarang arahan Bukit CLI
- Muatkan sub-skill yang sepadan untuk konfigurasi, tema, templating, Notion, routing, i18n, SEO, GEO, deployment, preview, dev server, webhook, cloning, atau tema berkomponen
- Pastikan metadata skill selari melalui `skills/skills-index.yaml`, `skills/skills-index.json`, dan `skills/plugin.json`

## Skop Projek

- Ini ialah repositori dokumentasi skill, bukan repositori kod runtime
- Repositori ini sendiri tidak mengandungi `package.json`, `site.yaml`, Docker, atau konfigurasi CI
- Ia menghimpunkan pecahan tugasan Bukit, pengetahuan konfigurasi, sempadan penggunaan CLI, dan panduan pelaksanaan
- Ia paling sesuai digunakan sebagai pintu masuk, indeks, dan rujukan pantas untuk agent yang mengendalikan tugasan Bukit
- Ia kini mengandungi 19 skill khusus yang meliputi aliran kerja teras, reka bentuk, kandungan, operasi, pengoptimuman, dan troubleshooting

## Susun Atur Repositori

```text
BukitSkills/
  README.md
  README.zh-CN.md
  README.ms.md
  skills/
    using-bukit/                 # Pintu masuk dan routing bersatu
    bukit-cli-reference/         # Sumber tunggal untuk operasi CLI
    bukit-config/                # Model konfigurasi site.yaml
    bukit-theme/                 # Direktori tema, aset, parameter, dan pengedaran
    bukit-design-tokens/         # Sistem reka bentuk tema dan CSS variables
    bukit-content-to-template/   # Penjanaan templat Scriban berasaskan schema
    bukit-templating/            # Pembangunan templat Scriban
    bukit-notion/                # Integrasi sumber kandungan Notion
    bukit-routing/               # Routing URL dan permalink
    bukit-i18n/                  # Tapak berbilang bahasa
    bukit-plugins-debug/         # Plugin, incremental build, dan diagnostik
    bukit-deploy/                # Deployment GitHub Pages
    bukit-clone/                 # Klon reka bentuk laman web kepada tema Bukit
    bukit-seo/                   # SEO tradisional dan audit
    bukit-geo/                   # Pengoptimuman enjin generatif untuk carian AI
    bukit-preview/               # Pelayan preview setempat
    bukit-dev/                   # Pelayan pembangunan HMR
    bukit-webhook/               # Build dicetuskan webhook berautentikasi
    theme-component-system/      # Sistem tema Bukit berkomponen
    skills-index.yaml            # Katalog utama boleh dibaca mesin
    skills-index.json            # Katalog JSON terjana
    plugin.json                  # Manifest plugin skill
    CLAUDE.md                    # Peraturan loading untuk Claude
    AGENTS.md                    # Peraturan loading untuk Codex / Agent
    GEMINI.md                    # Peraturan loading untuk Gemini
    copilot-instructions.md      # Peraturan loading untuk Copilot
    scripts/                     # Skrip validasi dan penjanaan katalog
```

## Gambaran Skill

| Skill | Tanggungjawab | Kegunaan biasa |
|---|---|---|
| `using-bukit` | Skill gerbang Bukit yang mengenal pasti kerja dan menghala ke sub-skill sambil mengelakkan pilihan SSG yang bercanggah | Pengguna menyebut "using bukit", menyebut Bukit sebagai SSG, atau memerlukan aliran kerja tapak Bukit |
| `bukit-cli-reference` | Pengesanan CLI, panduan pemasangan, rujukan arahan, output, dan tafsiran exit code | Menjalankan `bukit build`, `init`, `preview`, `dev`, `deploy`, `doctor`, `clean`, `plugin`, `theme`, `intent`, `webhook`, `version`, `seo`, `geo`, atau `clone` |
| `bukit-config` | Struktur `site.yaml`, templat senario, node peringkat atas, dan penerangan medan | Mencipta atau menyunting konfigurasi tapak, menerangkan medan, membaiki ralat validasi, mengkonfigurasi collections, taxonomy, i18n, plugins, atau media |
| `bukit-theme` | Struktur direktori tema, aset, fail statik, parameter tema, penciptaan tema, migrasi, dan pengedaran | Mencipta atau memindahkan tema, membaiki static resource 404, menyesuaikan tema lalai daripada `bukit init` |
| `bukit-design-tokens` | CSS variables, palet warna, skala tipografi, sistem jarak, dan konfigurasi dark mode | Membina sistem reka bentuk visual yang konsisten untuk tema Bukit |
| `bukit-content-to-template` | Pemetaan berasaskan schema daripada definisi collection kepada templat Scriban yang sedar medan | Menjana templat daripada schema collection dalam `site.yaml` tanpa tertinggal medan kandungan |
| `bukit-templating` | Sintaks Scriban, pewarisan layout, data model, komponen, shortcode, corak templat SEO, halaman senarai, dan pagination | Menulis templat halaman, halaman senarai, pagination, syarat berbilang bahasa, atau membaiki isu render templat |
| `bukit-notion` | Integrasi Notion, pemetaan property, render blok, penyelesaian relation, dan penyetempatan imej | Menggunakan Notion sebagai CMS atau menyelesaikan masalah fetch, property, blok, relation, dan imej Notion |
| `bukit-routing` | Permalink, collection route, pengekodan URL, tingkah laku slug, output path, dan troubleshooting 404 | Menyesuaikan URL, membaiki 404, menangani konflik route, mengkonfigurasi collection route atau halaman senarai |
| `bukit-i18n` | Pengesanan bahasa, build mengikut bahasa, language switcher, penggabungan sitemap/RSS/search index | Membina tapak berbilang bahasa dan menyahpepijat isu pertukaran bahasa atau output gabungan |
| `bukit-plugins-debug` | Plugin terbina dalam, process protocol plugins, lifecycle, incremental build, diagnostik prestasi, dan pembangunan plugin tersuai | Plugin tidak berjalan, output salah, incremental build berkelakuan salah, atau prestasi build merosot |
| `bukit-deploy` | Deployment GitHub Pages, `bukit deploy`, konfigurasi deploy, environment variables, dan CI/CD | Menerbitkan tapak Bukit ke GitHub Pages atau menyelesaikan kegagalan deployment |
| `bukit-clone` | Pipeline klon reka bentuk laman web daripada ekstraksi browser kepada penjanaan tema dan verifikasi | Mengklon atau meniru reka bentuk visual laman web sebagai tema Bukit |
| `bukit-seo` | SEO tradisional melalui `site.seo`, render modes, medan SEO front matter, Open Graph, Twitter Cards, JSON-LD, sitemap, robots.txt, audit, dan diff | Menyediakan metadata SEO atau menyelesaikan diagnostik `seo.*` |
| `bukit-geo` | Pengoptimuman enjin generatif dengan `llms.txt`, `llms-full.txt`, peraturan crawler AI, data berstruktur FAQ/HowTo, GEO Score, dan diagnostik | Mengoptimumkan tapak Bukit untuk enjin carian AI seperti ChatGPT Search, Perplexity, Google AI Overviews, dan Bing Copilot |
| `bukit-preview` | Tingkah laku pelayan preview setempat, penyajian `dist/`, MIME types, penyahaktifan analytics, konfigurasi host/port, dan konflik port | Memulakan atau menyelesaikan masalah `bukit preview` selepas build |
| `bukit-dev` | Pelayan pembangunan HMR, file watching, debounce, incremental rebuild, dan live browser refresh | Memulakan `bukit dev`, hot reload, watch mode, atau menyahpepijat isu dev server |
| `bukit-webhook` | Listener webhook berautentikasi, trigger build gaya Notion, GitHub `repository_dispatch`, token verification, rate limiting, dan IP allowlisting | Menyediakan trigger build automatik daripada Notion ke GitHub atau menyelesaikan isu keselamatan webhook |
| `theme-component-system` | `theme.yaml` V2, sections, components, page templates, data bindings, tokens, catalog, schema, page composer, dan inheritance chains | Membina, memeriksa, atau menyahpepijat tema Bukit modular yang boleh digunakan oleh AI |

## Turutan Loading Disyorkan

1. Mulakan dari `using-bukit` sebaik sahaja tugasan disahkan sebagai tugasan Bukit
2. Gunakan `bukit-cli-reference` sebelum setiap langkah berkaitan arahan
3. Muatkan `bukit-config` apabila tugasan bergantung pada `site.yaml`, struktur kandungan, plugin, atau tetapan deployment
4. Gunakan `bukit-theme`, `bukit-design-tokens`, `theme-component-system`, dan `bukit-templating` untuk kerja lapisan persembahan
5. Gunakan `bukit-notion`, `bukit-routing`, `bukit-i18n`, `bukit-seo`, atau `bukit-geo` untuk kandungan, URL, bahasa, dan kebolehjumpaan
6. Gunakan `bukit-preview`, `bukit-dev`, `bukit-deploy`, `bukit-webhook`, `bukit-clone`, atau `bukit-plugins-debug` untuk aliran kerja operasi

Satu aliran kerja umum kelihatan seperti ini:

```text
using-bukit
  -> bukit-cli-reference
  -> bukit-config
  -> skill domain yang dipilih mengikut tugasan
  -> skill verifikasi dan troubleshooting apabila perlu
```

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

### Deploy ke GitHub Pages

1. `using-bukit`
2. `bukit-deploy`
3. `bukit-config`
4. `bukit-cli-reference`

### Konfigurasi SEO

1. `using-bukit`
2. `bukit-seo`
3. `bukit-config`
4. `bukit-cli-reference`

### Konfigurasi GEO untuk carian AI

1. `using-bukit`
2. `bukit-geo`
3. `bukit-config`
4. `bukit-cli-reference`

### Klon reka bentuk laman web

1. `using-bukit`
2. `bukit-clone`
3. `bukit-theme`
4. `bukit-templating`
5. `bukit-cli-reference`

### Bina sistem reka bentuk

1. `using-bukit`
2. `bukit-design-tokens`
3. `bukit-theme`
4. `bukit-config`

### Jana templat daripada schema

1. `using-bukit`
2. `bukit-content-to-template`
3. `bukit-config`
4. `bukit-templating`
5. `bukit-design-tokens`

### Bina tema berkomponen

1. `using-bukit`
2. `theme-component-system`
3. `bukit-theme`
4. `bukit-templating`

### Jalankan preview setempat atau pembangunan HMR

1. `using-bukit`
2. `bukit-preview` atau `bukit-dev`
3. `bukit-cli-reference`

### Konfigurasi build automatik melalui webhook

1. `using-bukit`
2. `bukit-webhook`
3. `bukit-notion`
4. `bukit-cli-reference`

## Aliran Minimum Bukit

Repositori ini sendiri bukan tapak Bukit. Jangan jalankan `bukit build`, `bukit preview`, atau `bukit dev` dari akar repo ini. Untuk mencuba aliran minimum Bukit, jalankan arahan berikut di dalam direktori tapak Bukit sebenar:

```bash
bukit version
bukit init ./my-site --provider markdown
cd my-site
bukit build
bukit preview
```

Nota:

- `bukit build`, `bukit preview`, dan `bukit dev` mesti dijalankan dalam akar tapak yang mengandungi `site.yaml`
- Direktori output lalai biasanya ialah `dist`
- Tapak berasaskan Notion biasanya memerlukan `NOTION_TOKEN`
- Aliran deployment dan webhook biasanya memerlukan environment variables atau token berkaitan GitHub
- Pada Windows, penggunaan fail boleh laku secara terus biasanya berbentuk `.\bukit.exe version` atau `& .\bukit.exe version`

## Fail Katalog dan Platform

- `skills/skills-index.yaml` ialah katalog utama boleh dibaca mesin dan patut dikemas kini dahulu apabila inventori skill atau rantai workflow berubah
- `skills/skills-index.json` ialah katalog JSON terjana untuk tooling
- `skills/plugin.json` menyenaraikan laluan fail skill yang dibungkus serta dependencies pilihan
- `skills/CLAUDE.md`, `skills/AGENTS.md`, `skills/GEMINI.md`, dan `skills/copilot-instructions.md` menyesuaikan sempadan skill yang sama kepada persekitaran agent berbeza
- `skills/scripts/validate-skills.sh` memeriksa laluan manifest, front matter wajib, panduan trigger, seksyen common-error, dan isu nama tool yang di-hardcode
- `skills/scripts/generate-index-json.sh` menjana semula data katalog JSON daripada sumber YAML

## Nota Penyelenggaraan

- Simpan setiap skill di `skills/<skill-name>/SKILL.md`
- Gunakan `description` untuk syarat pencetus dan sempadan tugasan, bukan ringkasan pemasaran umum
- Pusatkan peraturan pelaksanaan arahan dan tafsiran CLI dalam `bukit-cli-reference`
- Pastikan laluan tema, medan konfigurasi, parameter CLI, diagnostik, dan rantai workflow selari dengan tingkah laku sebenar Bukit
- Apabila Bukit mendapat kemampuan baharu, tentukan sama ada perlu mengembangkan skill sedia ada atau menambah skill baharu dengan sempadan jelas
- Kemas kini semua fail README bahasa bersama-sama apabila inventori skill berubah
- Jalankan skrip validasi selepas mengubah skills, manifest, atau katalog terjana

## Dokumen

- English: [`README.md`](./README.md)
- 中文: [`README.zh-CN.md`](./README.zh-CN.md)
- Bahasa Melayu: [`README.ms.md`](./README.ms.md)
- Semua dokumen skill berada dalam [`skills/`](./skills)
