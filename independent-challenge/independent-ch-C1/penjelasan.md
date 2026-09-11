# Penjelasan Penggunaan Elemen Semantik HTML5

Berikut adalah alasan pemilihan elemen `article`, `section`, dan `time` pada halaman artikel kegiatan kampus:

1. **`<article>`**
   Elemen `<article>` digunakan untuk membungkus keseluruhan konten berita atau artikel (dari judul hingga footer artikel). Alasan utamanya adalah konten ini merupakan satu kesatuan informasi yang utuh, berdiri sendiri (independent), dan memiliki makna yang lengkap meskipun dilepaskan dari konteks halaman web aslinya (misalnya jika didistribusikan ulang via RSS feed).

2. **`<section>`**
   Elemen `<section>` digunakan untuk mengelompokkan bagian-bagian spesifik di dalam artikel, yaitu "Latar Belakang" dan "Rangkaian Kegiatan". Setiap `<section>` disertai dengan heading (`<h2>`) untuk mempertegas struktur hierarki informasi. Hal ini membantu pembaca dan *screen reader* memahami pembagian topik dalam artikel tersebut secara logis.

3. **`<time>`**
   Elemen `<time>` digunakan untuk membungkus waktu publikasi artikel ("12 September 2026, pukul 09.00 WIB"). Dengan menggunakan elemen ini beserta atribut `datetime="2026-09-12T09:00:00+07:00"`, kita memberikan format waktu terstandarisasi yang *machine-readable* (dapat dibaca oleh mesin). Ini sangat berguna bagi mesin pencari (SEO) dan aplikasi agregator untuk mengidentifikasi kapan tepatnya artikel tersebut dipublikasikan tanpa harus menebak format teks yang ditulis untuk manusia.
