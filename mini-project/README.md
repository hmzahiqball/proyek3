# MentorMate

## Deskripsi

Landing page statis untuk **MentorMate** — program mentoring mahasiswa yang membantu menemukan mentor sesuai kebutuhan akademik, skill, organisasi, dan karier.

Tagline: *"Temukan Mentor. Kembangkan Potensimu."*

## Target Pengguna

Mahasiswa yang membutuhkan mentor untuk pengembangan akademik, skill, organisasi, dan karier.

## Tujuan

Menjelaskan value proposition MentorMate dan mengarahkan pengunjung ke primary CTA "Temukan Mentor".

## Teknologi

- HTML5
- CSS3

Tidak menggunakan JavaScript, Bootstrap, Tailwind, atau framework/library lainnya.

## Struktur Project

```
mini-project/
├── index.html          # Halaman utama landing page
├── README.md           # Dokumentasi project
├── css/
│   └── style.css       # Stylesheet eksternal
└── assets/             # Folder untuk aset (jika diperlukan)
```

## Fitur / Section

| Section                  | ID              | Deskripsi                                      |
| ------------------------ | --------------- | ---------------------------------------------- |
| Header / Navigation      | —               | Logo, 3 link internal, CTA kecil               |
| Hero                     | `#home`         | Headline, tagline, CTA utama, ilustrasi CSS    |
| Benefits                 | `#benefits`     | 3 benefit cards menggunakan Flexbox             |
| How It Works             | `#how-it-works` | 3 langkah memulai program                      |
| Supporting Information   | `#why-mentoring`| Value proposition tambahan dengan statistik     |
| CTA                      | `#cta`          | Call-to-action section final                    |
| Footer                   | —               | Branding, navigasi footer, copyright            |

## Responsive Design

Website dirancang responsive untuk viewport mulai dari **320px** hingga **desktop (1440px+)**.

Breakpoint yang digunakan:

- **Default**: Mobile (320px+)
- **768px**: Tablet — layout dua kolom pada hero dan why-mentoring, steps horizontal
- **1024px**: Desktop — typography lebih besar, spacing lebih luas

Pada mobile:
- Navigation wrap secara natural tanpa overflow
- Hero berubah menjadi satu kolom
- Cards stack secara vertikal
- Tidak ada horizontal scrolling

## Accessibility

- `lang="id"` pada elemen `<html>`
- **Semantic HTML**: `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`
- **Heading hierarchy**: satu `<h1>`, `<h2>` untuk setiap section, `<h3>` untuk cards
- `aria-label` pada navigasi utama dan footer
- `aria-hidden="true"` pada elemen dekoratif (emoji, angka langkah, ilustrasi)
- **focus-visible** pada semua elemen interaktif (link dan button)
- Outline yang terlihat jelas, termasuk pada background gelap (CTA section dan footer)
- Contrast yang memadai antara teks dan background

## CSS Highlights

- **CSS Variables** untuk design tokens (warna, spacing, radius)
- **Flexbox** dengan `flex-wrap` untuk benefit cards
- **Mobile-first** responsive approach
- `box-sizing: border-box` pada semua elemen
- Reusable `.container` dengan `min()` dan `margin-inline: auto`
- Tidak menggunakan `!important`
- Tidak menggunakan inline style
- Smooth scroll via `scroll-behavior: smooth`

## Testing Checklist

- [ ] HTML validator (tidak ada error utama)
- [ ] Semua internal links mengarah ke ID yang valid
- [ ] Responsive 320px (tidak ada horizontal overflow)
- [ ] Responsive 768px
- [ ] Desktop (1440px)
- [ ] Keyboard focus terlihat pada semua link dan button
- [ ] Tidak ada horizontal overflow di semua viewport
- [ ] Tidak ada inline style di HTML
- [ ] Tidak ada `!important` di CSS
- [ ] Flexbox dengan `flex-wrap` pada benefit cards

## Refleksi

> *Bagian ini dapat diisi setelah pengerjaan selesai.*

- Apa yang saya pelajari dari project ini?
- Apa tantangan utama yang saya hadapi?
- Apa yang akan saya lakukan berbeda jika mengerjakan ulang?
- Bagian mana yang paling sulit dikerjakan?
- Apa hal baru yang saya temukan saat mengerjakan project ini?
