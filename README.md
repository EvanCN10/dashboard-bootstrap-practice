# dashboard-bootstrap-practice

# Proyek Dashboard Smart Farming 🌿

Ini adalah proyek front-end sederhana yang dibuat untuk tugas mata kuliah pemrograman web. Proyek ini bertujuan untuk membuat sebuah dashboard monitoring "Smart Farming" berdasarkan desain yang diberikan, dengan menggunakan **HTML** dan framework **Bootstrap 5**.

## 📸 Tampilan Hasil

Berikut adalah tampilan akhir dari dashboard yang berhasil dibuat.

![Screenshot Dashboard](https://i.imgur.com/L08zUnc.png)

---

## ✨ Fitur Utama

-   **Desain Responsif**: Tampilan dashboard dapat menyesuaikan diri dengan baik di berbagai ukuran layar, mulai dari desktop hingga perangkat mobile.
-   **Kartu Data Sensor**: Menampilkan berbagai parameter data (seperti kelembaban, suhu, pH, dll.) dalam format kartu yang mudah dibaca.
-   **Indikator Visual**:
    -   Setiap kartu memiliki **garis warna** di sisi kiri untuk membedakan kategori data.
    -   Beberapa kartu dilengkapi dengan **progress bar** untuk visualisasi level data.
-   **Modern & Bersih**: Menggunakan komponen dan utility class dari Bootstrap 5 untuk tampilan yang modern.
-   **Ringan**: Proyek ini murni front-end (HTML & CSS) dan tidak memerlukan server atau dependensi yang rumit untuk dijalankan.

---

## 🛠️ Teknologi yang Digunakan

-   **HTML5**: Sebagai struktur dasar halaman web.
-   **CSS3**: Untuk styling kustom seperti warna border dan efek hover.
-   **Bootstrap 5**: Sebagai framework utama untuk layout, komponen (kartu, progress bar), dan responsivitas.
-   **Font Awesome (Opsional)**: Untuk ikon-ikon yang mempercantik tampilan kartu.

---

## 🚀 Cara Menjalankan Proyek

Karena ini adalah proyek statis, kamu tidak perlu melakukan instalasi apa pun. Cukup ikuti langkah berikut:

1.  Pastikan kamu memiliki file `index.html`.
2.  Buka file `index.html` tersebut menggunakan browser web apa pun (misalnya Google Chrome, Firefox, atau Microsoft Edge).
3.  Selesai! Dashboard akan langsung ditampilkan.

---

## 🧐 Penjelasan Kode

Kode ini dirancang agar mudah dipahami dengan memanfaatkan kelas-kelas bawaan Bootstrap.

### 1. **Struktur Dasar & Koneksi Bootstrap**
Di dalam tag `<head>`, kita menghubungkan file CSS Bootstrap dari CDN (Content Delivery Network). Ini cara termudah untuk menggunakan Bootstrap tanpa harus mengunduh file-nya secara manual.

```html
<link href="[https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css](https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css)" rel="stylesheet">
```

### 2. **Layout Utama**
Layout dibuat menggunakan sistem grid Bootstrap.
-   `container-fluid`: Membuat wadah utama yang lebarnya 100%.
-   `row`: Digunakan sebagai pembungkus baris untuk kartu-kartu sensor.
-   `col-lg-2 col-md-4 mb-4`: Ini adalah kunci responsivitas.
    -   Di layar besar (`lg`), satu kartu akan memakan 2 dari 12 kolom (sehingga 1 baris muat 6 kartu).
    -   Di layar medium (`md`), satu kartu memakan 4 dari 12 kolom (1 baris muat 3 kartu).
    -   Di layar kecil, kartu akan otomatis tersusun ke bawah (1 baris 1 kartu).

### 3. **Komponen Kartu (`.card`)**
Setiap data sensor ditampilkan dalam sebuah `div` dengan kelas `.card`.
-   **Garis Warna Kiri**: Dibuat dengan CSS kustom. Kelas seperti `.border-left-primary` menambahkan `border-left` dengan warna yang sesuai.
-   **Utility Classes**: Sebagian besar styling teks (seperti `fw-bold` untuk tebal, `text-uppercase` untuk kapital, dan `text-primary` untuk warna) menggunakan kelas utility dari Bootstrap untuk mempercepat proses development.

```html
<div class="card border-left-primary h-100 py-2">
    <div class="card-body">
        <div class="text-xs fw-bold text-primary text-uppercase mb-1">KELEMBABAN (RH%)</div>
        <div class="h5 mb-0 fw-bold">54 %</div>
    </div>
</div>
```

### 4. **Progress Bar**
Untuk kartu seperti "Kekeruhan", ikon digantikan dengan komponen `progress` dari Bootstrap untuk memberikan representasi visual dari nilai sensor.

```html
<div class="progress flex-grow-1" style="height: 10px;">
    <div class="progress-bar bg-info" role="progressbar" style="width: 18%"></div>
</div>
```

# Update 1.0 🔥
-   **Struktur HTML Baru**:
    Setiap `.card-body` kini memiliki dua `div` di dalamnya:
    1.  `<div class="card-content">`: Untuk membungkus konten asli (judul dan nilai sensor).
    2.  `<div class="card-description">`: Untuk membungkus teks deskripsi yang awalnya disembunyikan.

    ```html
    <div class="card-body">
        <div class="card-content">...</div>
        <div class="card-description">...</div>
    </div>
    ```

-   **Logika CSS**:
    -   Kelas `.card-description` diberi `opacity: 0` (transparan/tersembunyi) dan `position: absolute` (melayang di atas konten asli).
    -   Saat `.card` di-hover (`.card:hover`), kita mengubah `opacity` pada `.card-description` menjadi `1` (terlihat) dan `opacity` pada `.card-content` menjadi `0` (tersembunyi).
    -   Properti `transition` digunakan pada kedua kelas tersebut untuk menciptakan efek animasi muncul/menghilang yang mulus.
