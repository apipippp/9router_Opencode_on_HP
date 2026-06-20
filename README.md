🚀 Instalasi Ubuntu Proot + Node.js + 9router + OpenCode di Termux

Panduan lengkap untuk menjalankan Ubuntu Proot, Node.js, 9router, dan OpenCode di Android menggunakan Termux.

---

📋 Prasyarat

- Termux terbaru
- Koneksi internet stabil
- Ruang penyimpanan minimal 5 GB

---

1️⃣ Persiapan Termux

Update package Termux:

pkg update && pkg upgrade -y

Install package yang dibutuhkan:

pkg install proot-distro curl wget git -y

---

2️⃣ Install Ubuntu dengan Proot-Distro

Install Ubuntu:

proot-distro install ubuntu

Masuk ke Ubuntu:

proot-distro login ubuntu

Cek versi Ubuntu:

cat /etc/os-release

Contoh output:

PRETTY_NAME="Ubuntu 24.04 LTS"

---

3️⃣ Update Ubuntu

Karena kita sudah login sebagai root, tidak perlu menggunakan "sudo".

Update package Ubuntu:

apt update && apt upgrade -y

Install package dasar:

apt install curl wget git build-essential ca-certificates -y

---

4️⃣ Install Node.js dari NodeSource

«⚠️ Disarankan menggunakan Node.js dari NodeSource agar terhindar dari masalah dependency pada paket bawaan Ubuntu.»

Tambahkan repository NodeSource:

curl -fsSL https://deb.nodesource.com/setup_22.x | bash -

Install Node.js:

apt install nodejs -y

Verifikasi instalasi:

node -v
npm -v

Contoh output:

v22.x.x
10.x.x

---

5️⃣ Install 9router

Install secara global:

npm install -g 9router

Verifikasi:

9router --help

---

6️⃣ Install OpenCode

Install secara global:

npm install -g opencode-ai

Verifikasi:

opencode --help

---

7️⃣ Menyimpan Project di Storage Android

Agar project dapat diakses dari:

- ZArchiver
- Acode
- VS Code Android
- File Manager Android

gunakan folder Documents Android.

Masuk ke folder Documents:

cd /sdcard/Documents

Buat folder project:

mkdir project
cd project

Clone repository:

git clone <url-repository>

Contoh:

git clone https://github.com/user/repo.git

---

8️⃣ Cara Masuk Kembali ke Ubuntu

Dari Termux:

proot-distro login ubuntu

---

9️⃣ Cara Keluar dari Ubuntu

exit

---

🔧 Troubleshooting

npm Error atau Dependency Rusak

Hapus Node.js bawaan Ubuntu:

apt purge nodejs npm -y
apt autoremove -y

Kemudian ulangi langkah instalasi NodeSource.

---

Tidak Bisa Akses File dari ZArchiver

Gunakan salah satu lokasi berikut untuk menyimpan source code dan project:

/sdcard/Documents

atau

~/storage/documents

«⚠️ Jangan memindahkan seluruh filesystem Ubuntu ke Documents.

Filesystem Android tidak mendukung seluruh fitur Linux seperti:

- Symbolic Link (symlink)
- Permission Linux
- Device Files

yang dibutuhkan oleh Ubuntu Proot.»

---

⚡ Ringkasan Instalasi Cepat

pkg update && pkg upgrade -y
pkg install proot-distro curl wget git -y

proot-distro install ubuntu
proot-distro login ubuntu

apt update && apt upgrade -y
apt install curl wget git build-essential ca-certificates -y

curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt install nodejs -y

npm install -g 9router
npm install -g opencode-ai

---

✅ Selesai

Sekarang Ubuntu Proot telah siap digunakan dengan:

- Ubuntu Proot
- Node.js
- npm
- 9router
- OpenCode

Selamat ngoding di Android! 🎉
