# General Static Website Deployer (RADFWorkflow)

Selamat datang di repositori **General Static Website Deployer**. Repositori ini tidak berisi kode website, melainkan berfungsi sebagai **pusat kendali CI/CD (Continuous Integration/Continuous Deployment)** untuk semua proyek website statis Anda di GitHub.

Tujuannya adalah untuk memiliki satu workflow yang kuat dan dapat digunakan kembali untuk memeriksa kualitas, memindai keamanan, dan mendeploy website statis apa pun yang ada di akun Anda dengan beberapa klik saja.

---

## ✨ Fitur Utama Workflow

Alur kerja (`.github/workflows/deploy.yml`) yang ada di repositori ini dirancang untuk menjadi lebih dari sekadar deployer. Ia adalah penjaga kualitas dan keamanan otomatis Anda.

-   **Reusable (Dapat Digunakan Kembali):** Satu workflow untuk mendeploy jumlah repositori yang tidak terbatas.
-   **Pemeriksaan Kualitas Kode:** Menggunakan **Super-Linter** untuk secara otomatis memeriksa file HTML, CSS, dan JavaScript Anda terhadap praktik terbaik dan potensi error.
-   **Pemindaian Keamanan Statis (SAST):** Menggunakan **GitHub CodeQL** untuk menganalisis kode Anda dan mencari potensi kerentanan keamanan umum (seperti XSS).
-   **Pemeriksaan Tautan Rusak:** Secara otomatis memindai seluruh situs Anda untuk memastikan tidak ada tautan internal atau eksternal yang rusak.
-   **Deployment Sekali Klik:** Proses deployment yang aman dan andal ke GitHub Pages melalui antarmuka GitHub Actions.

---

## 🛠️ Prasyarat: Setup Satu Kali

Sebelum menggunakan workflow ini untuk pertama kalinya, Anda perlu melakukan setup satu kali untuk memberikan izin kepada workflow ini agar dapat mengakses repositori Anda yang lain.

### 1. Buat Personal Access Token (PAT)

Workflow ini memerlukan token untuk meng-kloning repositori privat maupun publik Anda.

1.  Buka **Settings** GitHub Anda (klik foto profil di pojok kanan atas).
2.  Navigasi ke **Developer settings** > **Personal access tokens** > **Tokens (classic)**.
3.  Klik **"Generate new token"** > **"Generate new token (classic)"**.
4.  Beri nama yang jelas, misalnya `GENERAL_DEPLOYER_TOKEN`.
5.  Atur **Expiration** sesuai kebutuhan Anda (misalnya, 90 hari).
6.  Di bagian **"Select scopes"**, centang kotak **`repo`**. Ini akan memberikan semua izin yang diperlukan.
7.  Klik **"Generate token"**.
8.  **Salin token yang muncul.** Anda tidak akan bisa melihatnya lagi.

### 2. Simpan Token sebagai Repository Secret

1.  Kembali ke repositori `Official-idn/RADFWorkflow` ini.
2.  Buka **Settings** > **Secrets and variables** > **Actions**.
3.  Klik tombol **"New repository secret"**.
4.  Masukkan informasi berikut:
    -   **Name:** `CHECKOUT_TOKEN`
    -   **Secret:** Tempelkan Personal Access Token yang baru saja Anda salin.
5.  Klik **"Add secret"**.

---

## 🚀 Cara Mendeploy Website Baru

Setiap kali Anda ingin mendeploy atau memperbarui salah satu website statis Anda, ikuti tiga langkah mudah ini:

### Langkah 1: Push Perubahan Terbaru
Pastikan semua perubahan kode terbaru sudah Anda `push` ke repositori website yang bersangkutan (misalnya, ke `Official-idn/danuferdian`).

### Langkah 2: Jalankan Workflow Secara Manual
1.  Di repositori `RADFWorkflow` ini, klik tab **"Actions"**.
2.  Di menu sebelah kiri, klik workflow **"General Static Website Deployer"**.
3.  Klik tombol **"Run workflow"** di sisi kanan.

### Langkah 3: Masukkan Repositori Target
1.  Sebuah dropdown akan muncul.
2.  Di dalam input field **"Repositori yang akan di-deploy"**, ketikkan nama lengkap repositori target dalam format `username/nama-repo`.
    -   **Contoh:** `Official-idn/danuferdian`
3.  Pastikan Anda memilih *branch* yang benar (biasanya `main`).
4.  Klik tombol hijau **"Run workflow"**.

Proses akan dimulai. Anda bisa mengklik workflow yang sedang berjalan untuk melihat log secara *real-time*. Setelah selesai, website Anda akan diperbarui di URL GitHub Pages yang terkait dengan repositori `RADFWorkflow` ini.

---

## 🌐 Konfigurasi GitHub Pages (Satu Kali)

Untuk memastikan website Anda tayang, pastikan GitHub Pages di repositori `RADFWorkflow` ini sudah dikonfigurasi dengan benar:

1.  Buka **Settings** di repositori `RADFWorkflow`.
2.  Navigasi ke **Pages**.
3.  Di bawah "Build and deployment", pastikan **Source** diatur ke **"GitHub Actions"**.

URL publik Anda akan ditampilkan di halaman ini.
