# 🌍 Portal Data Sistem Pendidikan Luar Negeri (SPLN)

Portal web interaktif untuk melihat, mencari, dan menambahkan data komprehensif mengenai sistem pendidikan, kurikulum, kalender akademik, serta kontak perwakilan pendidikan Indonesia (KBRI/KJRI) di berbagai negara.

![SPLN Web Preview](https://via.placeholder.com/1000x500.png?text=Screenshot+Website+SPLN) *(Silakan ganti link gambar ini dengan screenshot asli website Anda)*

## ✨ Fitur Utama

- **🚀 Real-time Data Fetching:** Mengambil data langsung dari Google Sheets (Published to Web) secara *real-time*.
- **🔍 Pencarian Cerdas:** Filter data berdasarkan nama negara atau nama KBRI/KJRI secara instan (Client-side search).
- **📝 Seamless Form Integration:** Form input data terhubung langsung dengan Google Forms menggunakan teknik *Hidden Iframe*, sehingga *user* tidak dilempar (redirect) ke halaman Google setelah *submit*.
- **📱 Desain Responsif:** Tampilan UI/UX modern berbasis Card yang dirancang sepenuhnya *Mobile-Friendly*.
- **🪄 Fitur "Load Sample Data":** Memudahkan *testing* form dengan 1-klik pengisian data *dummy*.

## 🛠️ Teknologi yang Digunakan

Proyek ini dibangun menggunakan arsitektur *Serverless* murni yang sangat ringan tanpa perlu *backend deployment*:

- **Frontend:** HTML5, CSS3, JavaScript (Vanilla/ES6)
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) (via CDN)
- **Ikon:** [Phosphor Icons](https://phosphoricons.com/)
- **Database (Read):** Google Sheets API (Export to CSV)
- **Database (Write):** Google Forms (POST via HTML Form action)

## ⚙️ Cara Kerja Sistem (Arsitektur)

Sistem ini menggunakan ekosistem Google Workspace sebagai "Backend" dan "Database":
1. **READ (Membaca Data):** Website men-download file CSV dari URL *Google Sheet* yang telah di-*publish*. JavaScript akan mem-*parsing* CSV tersebut menjadi format JSON dan me-rendernya menjadi *Card* ke layar browser.
2. **WRITE (Menulis Data):** Saat *user* mengisi data baru, tag `<form>` di HTML akan menembak (POST) langsung ke URL `formResponse` milik *Google Form*. Target *submit* diarahkan ke sebuah `<iframe>` yang disembunyikan agar halaman web tidak beralih.

## 🚀 Cara Menjalankan secara Lokal

1. **Clone repositori ini:**
   ```bash
   git clone https://github.com/USERNAME_ANDA/NAMA_REPO_ANDA.git


   Buka folder project:
code
Bash
cd NAMA_REPO_ANDA
Jalankan file HTML:
Tidak perlu instalasi Node.js, NPM, atau server khusus. Anda hanya perlu klik ganda file index.html untuk membukanya di browser, atau gunakan ekstensi VS Code seperti Live Server untuk pengalaman pengembangan yang lebih baik.
🔗 Konfigurasi Google Form & Sheets (Bagi Developer Lain)
Jika Anda ingin fork repo ini dan menggunakan database/form Anda sendiri, ikuti langkah berikut:
1. Setup Database (Google Sheets)
Buat Google Form terlebih dahulu beserta pertanyaannya (Pastikan TIDAK ada pertanyaan "File Upload" dan matikan fitur "Require Sign In" di pengaturan).
Buka tab "Responses" di form tersebut, dan hubungkan (Link to Sheets) untuk membuat Google Sheet.
Buka Google Sheet tersebut, klik File > Share > Publish to web.
Pilih Entire Document dan format Comma-separated values (.csv), lalu klik Publish.
Salin link CSV tersebut dan paste ke variabel sheetUrl di dalam fungsi fetchSPLNData() pada file index.html.
2. Setup Input Data (Google Forms)
Dapatkan URL Form Submit: Dapatkan link respons form Anda yang berakhiran .../formResponse dan jadikan sebagai atribut action="..." pada form HTML.
Dapatkan ID Input (entry.XXXXX): Inspect element (F12) pada halaman preview Google Form asli Anda. Cari properti name pada masing-masing kotak input. Paste ID tersebut ke atribut name="entry.XXXX" di input HTML Anda.
🤝 Kontribusi
Pull request sangat dipersilakan. Untuk perubahan besar, harap buka issue terlebih dahulu untuk mendiskusikan apa yang ingin Anda ubah.
📄 Lisensi
MIT
code
Code
### Tips Tambahan Sebelum Commit:
1. Pastikan mengganti link gambar placeholder di bagian atas dengan link *screenshot* website Anda (bisa diupload ke repositori GitHub di folder `/assets` atau sekadar ditarik (*drag & drop*) di kolom komentar issue GitHub untuk mendapatkan link `.png`).
2. Ganti `USERNAME_ANDA` dan `NAMA_REPO_ANDA` pada langkah "Cara Menjalankan Secara Lokal" dengan *username* dan *repository name* GitHub asli Anda.
