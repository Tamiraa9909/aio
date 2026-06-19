<h1 align="center">
  ⚡ <span style="color:white">MEDIA</span><span style="color:#007BFF">FAIRY</span> AIO
</h1>

Repositori ini memuat skrip proksi *All-in-One* (VMess, VLESS, Trojan, Shadowsocks) yang dirancang untuk di-deploy secara otomatis ke **Cloudflare Pages** menggunakan integrasi GitHub Actions. Skrip ini mendukung penambahan *custom domain* massal secara otomatis.

---

## 🚀 Panduan Deployment

Ikuti 4 langkah utama di bawah ini untuk mengudara dalam hitungan menit.

### 1. Buat Project Cloudflare Pages (Tahap Inisiasi)
*Langkah ini wajib agar GitHub Actions memiliki target deployment.*

1. Login ke dashboard [Cloudflare](https://dash.cloudflare.com).
2. Navigasi ke menu **Workers & Pages** > klik **Create application** > tab **Pages**.
3. Pilih opsi **Upload assets** (Direct Upload).
4. Pada kolom **Project name**, ketik persis nama ini: `mediafairy-aio`.
5. Klik **Create project**.
6. Unggah satu file teks kosong apa saja (misal: `index.txt`) untuk memancing pembuatan *project*.
7. Klik **Deploy site**.

### 2. Dapatkan Kredensial Cloudflare
Anda membutuhkan token agar GitHub bisa berkomunikasi dengan Cloudflare Anda.

1. Catat **Account ID** Anda (terletak di halaman utama dashboard Cloudflare, bagian kanan bawah).
2. Pergi ke **My Profile** (ikon orang di pojok kanan atas) > pilih **API Tokens**.
3. Klik **Create Token** > gulir ke bawah dan pilih **Get started** (*Create Custom Token*).
4. Beri nama token, lalu set **Permissions** berikut:
   * `Account` | `Cloudflare Pages` | `Edit`
   * `Zone` | `DNS` | `Edit`
5. Lanjutkan dan klik **Create Token**. Salin token rahasia yang muncul.

### 3. Setup GitHub Secrets & Custom Domain (Bulk)

1. Pergi ke tab **Settings** > **Secrets and variables** > **Actions**.
2. Klik **New repository secret** dan tambahkan 3 kunci berikut secara berurutan:

| Nama Secret | Nilai (Value) |
| :--- | :--- |
| **`CLOUDFLARE_API_TOKEN`** | Paste token dari Langkah 2. |
| **`CLOUDFLARE_ACCOUNT_ID`** | Paste Account ID dari Langkah 2. |
| **`CUSTOM_DOMAIN`** | Masukkan domain Anda. **Bisa lebih dari 1 domain sekaligus!** Pisahkan dengan koma (`,`) atau koma dan spasi (`, `).<br>*Contoh: `vpn1.domain.com, vpn2.domain.com, bug.host.com`* |

### 4. Eksekusi Deployment
Setelah semua rahasia tersimpan, jalankan sistem automasinya.

1. Pergi ke tab **Actions** di repositori GitHub Anda.
2. Di sebelah kiri, klik *workflow* bernama **Deploy to Cloudflare Pages**.
3. Klik tombol **Run workflow** di sebelah kanan.
4. Tunggu prosesnya berjalan (1-2 menit). Jika berstatus ✅ hijau, proksi AIO dan semua *custom domain* Anda telah sukses di-deploy dan siap digunakan!

---

## 🛠️ Konfigurasi Klien 
Gunakan format *path* berikut pada pengaturan klien VPN Anda (v2rayN, Sing-box, NekoBox, dll) agar dapat terhubung dengan proksi ini:

**Path WebSocket (WS):**
```text
/mediafairy/ip:port
