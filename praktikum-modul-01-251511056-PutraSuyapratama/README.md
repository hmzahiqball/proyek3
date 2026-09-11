# Praktikum Modul 1 - Putra Suyapratama / 251511056

## Ringkasan halaman
Halaman ini adalah halaman profil portofolio pribadi statis yang dirancang secara semantik dan responsif. Dokumen HTML disusun menggunakan struktur yang bermakna seperti `<header>`, `<main>`, `<section>`, dan `<footer>`, menjauhi penggunaan `div` yang berlebihan (Task 1). Desain antarmuka (UI) dibangun dengan identitas visual yang konsisten menggunakan variabel CSS dan tipografi yang bersih (Task 2). Terakhir, sistem *layouting* diatur menggunakan pendekatan *mobile-first* dengan Flexbox agar susunan kartu profil menyesuaikan dimensi layar perangkat secara dinamis, dari tatanan vertikal di ponsel hingga jajaran grid horizontal di resolusi besar (Task 3).

## Tiga keputusan teknis
1. **Penerapan *Design Tokens* melalui CSS Custom Properties (`:root`)**
   Saya memutuskan untuk memusatkan pengelolaan variabel warna (seperti `--warna-utama: #0284c7`) dan ukuran (*spacing*) di dalam pseudo-class `:root`. Keputusan ini sangat berdampak pada skalabilitas dan perapihan (UI Polishing), karena perubahan satu nilai variabel akan merefleksikan perubahan ke seluruh komponen web (seperti navigasi dan tombol) secara bersamaan tanpa mencari-cari nilai *hardcode*.
2. **Pendekatan *Mobile-First* dengan Flexbox (`flex-direction: column`)**
   Daripada merancang *layout* desktop dan harus memaksa *override* kode untuk mobile, saya membiarkan bentuk awal `.card-list` menjadi baris bersusun satu kolom. CSS awal menjadi lebih ringan bagi perangkat kecil, dan kita cukup menerapkan *media query* tunggal pada `768px` untuk mengubahnya menjadi baris menyamping (`row`), meniadakan potensi *overflow* secara otomatis di awal pembuatan.
3. **Penerapan `box-sizing: border-box` Secara Global**
   Ini adalah keputusan mendasar yang menjaga keutuhan struktur. Dengan `box-sizing: border-box` pada semua elemen, ukuran tebal bingkai (border) dan *padding* (ruang kosong di dalam `.card`) akan dihitung ke dalam dimensi lebar total yang sudah ditetapkan. Hasilnya, ukuran `.card` tidak pernah melewati batas (*spill over*) yang memicu kemunculan *horizontal scrollbar*.

## Masalah, diagnosis, dan perbaikan
**Masalah 1:** Gambar profil saya awalnya melebar dan menjebol kontainer (muncul *horizontal scrollbar*) saat ukuran viewport diubah menjadi sangat kecil (320px).
**Diagnosis:** Elemen `<img>` bertindak sebagai *replaced element* yang memiliki lebar bawaan yang statis dan kaku jika tidak diinstruksikan sebaliknya.
**Perbaikan:** Saya menerapkan styling `max-width: 100%` dan `height: auto` pada tag gambar. Ini memaksa gambar untuk membatasi ukuran terbesarnya sebatas lebar kontainer induknya (di dalam `.card`), namun tetap mempertahankan rasio aslinya.

**Masalah 2:** Indikator fokus (fokus keyboard menggunakan tombol 'Tab') pada link navigasi dan tombol kontak bawaan browser seringkali kurang menonjol dan kontrasnya rendah terhadap background putih.
**Diagnosis:** Standar *outline* dari masing-masing browser berbeda-beda.
**Perbaikan:** Saya menerapkan pseudo-class `:focus-visible` secara manual di CSS pada elemen interaktif dengan memberikan *outline* tebal dengan gaya `outline: 2px solid var(--warna-utama)` serta ditambahkan `outline-offset: 4px` agar letak kotaknya lebih jelas.

## Hasil pengujian empat viewport
Pengujian responsivitas telah disimulasikan menggunakan *Chrome Device Toolbar*. File gambar bukti terdapat dalam direktori `evidence/`.
- **320px:** *Pass*. Tata letak membentuk 1 kolom solid. Gambar mengecil proporsional secara penuh di dalam card. Link menu navigasi melipat (wrap) secara elegan jika tidak cukup berjejer, menghindari luapan.
- **375px:** *Pass*. Struktur masih 1 kolom, namun ruang baca lebih lega. Tidak ada isu pemotongan karakter.
- **768px:** *Pass*. Pada *breakpoint* ini, *media query* tereksekusi. `.card-list` berpindah menjadi baris horizontal (*flex row*). Ketiga section berjajar rapi ke samping dengan dukungan `flex-wrap`.
- **1024px:** *Pass*. Lebar penampung konten (.container) dibatasi pada max-width `800px` dan terpusat (`margin: auto`). Layout terlihat elegan tanpa elemen yang meregang terlalu jauh.

## Refleksi belajar
Menyelesaikan tiga *Task* praktikum ini membangun pemahaman holistik tentang fondasi antarmuka modern. Penggunaan *Semantik HTML* tidak hanya membuahkan kode yang bersih tetapi juga mempermudah saat di-*styling* dengan CSS karena strukturnya sudah "bercerita". Pengaplikasian *Flexbox* mengubah konsep *layouting* tradisional saya yang sebelumnya terlalu rumit dan sering merusak elemen lain.
**Satu kesalahan yang membantu:**
Pada awal mencoba menjejalkan tiga section menjadi horizontal, saya sempat mencoba memberikan nilai `width: 30%` pada tiap kartu dengan `float` atau `inline-block`. Akibatnya jarak meleset, ukuran konten tidak seimbang, dan menumpuk saat layar dikecilkan. Kesalahan kuno ini membimbing saya untuk bersyukur dengan fitur `display: flex` dikombinasikan dengan `flex-basis`, membiarkan browser yang melakukan kalkulasi kompleks pendistribusian ruangnya.
**Area untuk ditingkatkan:**
Saya menyadari pengetahuan saya mengenai efisiensi penamaan class (metodologi CSS) masih dasar. Walau kode ini sukses, pada proyek raksasa kelak akan sulit menjaga spesifisitas. Saya ingin meningkatkan *skill* ini bersama penajaman transisi/animasi CSS agar halaman terasa lebih 'hidup' dan premium tanpa JavaScript tambahan.

## Log AI atau sumber bantuan

**Penggunaan AI (LLM):**

**Pertanyaan 1 (Debugging Overflow)**
*User:* "Bro, gambar profil gw sering nabrak keluar batas .card kalau viewport browsernya digeser jadi 320px, padahal lebarnya udah gw tentuin 150px. Gimana ya cara fix ini biar tetep responsif tapi ukurannya ga kebesaran?"
*Jawaban AI:* AI menganalisis bahwa penggunaan nilai fix/absolut (`150px`) memaksa lebar gambar konstan di ukuran sekecil apa pun. AI menyarankan untuk mereset perilakunya dengan memberikan atribut fleksibel `max-width: 100%; height: auto;`.
*Fact Check & Eksekusi:* Saya memvalidasi saran ini berdasarkan pedoman *Responsive Images* pada dokumentasi MDN Web Docs. Saya menulis dan memodifikasi sendiri kode tersebut di dalam selektor `.card img`, dan setelah di-refresh, masalah overflow seketika teratasi.

**Pertanyaan 2 (Penjelasan Worksheet Task 2)**
*User:* "Di worksheet, ada pertanyaan: 'Mengapa ukuran card tidak melebihi width setelah diberi padding?'. Gue tahu ini karena gw tambahin kode `box-sizing`, tapi bisa bantu rangkum alasannya gak buat gw jawab pertanyaannya secara logis? Soalnya gw mahasiswa yang lagi belajar CSS."
*Jawaban AI:* AI menerangkan secara simpel mengenai hierarki *Box Model*. Standar bawaan CSS (yaitu `content-box`) akan menambahkan besaran *padding* ke *width*, sehingga elemen melebar. Namun, *property* `box-sizing: border-box` menyuruh CSS menyusutkan area ruang konten (*content area*) guna menyisakan ruang bagi padding, sehingga *width* bingkai luar secara total tetap konstan.
*Fact Check & Eksekusi:* Untuk membuktikannya, saya membuka *DevTools* dan mengamati tab *Computed*. Terbukti secara visual pada kotak bahwa ukuran batas final tak bertambah walau padding diubah menjadi berapapun. Logika ini lalu saya tulis ulang dan rangkum sendiri untuk melengkapi laporan Worksheet Task 2.
