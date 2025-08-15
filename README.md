# RADFWorkflow
Security Scan, Quality Check, and Deploy, for Static HTML Website

Penjelasan Perubahan Kunci:
Nama: Diubah menjadi General Static Website Deployer agar lebih jelas.
Pemicu (on): Sekarang hanya menggunakan workflow_dispatch. Pemicu schedule dan push dihapus karena workflow ini tidak lagi terikat pada satu repositori spesifik.
inputs: Ini adalah tambahan baru yang paling penting. Ia membuat sebuah input field bernama target_repo.
repository: ${{ github.event.inputs.target_repo }}: Di setiap langkah checkout, nama repositori yang di-hardcode (Official-idn/danuferdian) diganti dengan variabel ini. Ini berarti workflow akan mengunduh kode dari repositori mana pun yang Anda ketikkan di input field.
Cara Menggunakannya (Alur Kerja Baru)
Sekarang, setiap kali Anda ingin mendeploy sebuah website (misalnya danuferdian atau website baru lainnya), alurnya akan seperti ini:
Pastikan Kode Terbaru Ada di Repositorinya.
Lakukan push semua perubahan terbaru Anda ke repositori website yang bersangkutan (misalnya, ke Official-idn/danuferdian).
Buka Repositori Workflow Anda.
Buka https://github.com/Official-idn/RADFWorkflow di browser.
Jalankan Workflow Secara Manual.
Klik tab "Actions".
Di menu sebelah kiri, klik workflow "General Static Website Deployer".
Anda akan melihat tombol "Run workflow". Klik tombol tersebut.
Isi Nama Repositori Target.
Sebuah dropdown akan muncul dengan sebuah input field bernama "Repositori yang akan di-deploy".
Di dalam kotak tersebut, ketikkan nama lengkap repositori yang ingin Anda deploy.
Contoh: Official-idn/danuferdian
Pastikan Anda memilih branch yang benar (biasanya main).
Klik Tombol Hijau "Run workflow".
Selesai! GitHub Actions sekarang akan mengambil kode dari repositori yang Anda tentukan (danuferdian), menjalankannya melalui semua pemeriksaan kualitas dan keamanan, lalu mendeploy hasilnya ke GitHub Pages yang terkait dengan repositori RADFWorkflow.
Dengan ini, repositori RADFWorkflow Anda telah menjadi pusat kendali yang kuat untuk mendeploy semua proyek website statis Anda.
