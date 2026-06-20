Instalasi Ubuntu Proot + Node.js + 9router + OpenCode di Termux

1. Persiapan Termux

Update package Termux:

pkg update && pkg upgrade -y

Install package yang dibutuhkan:

pkg install proot-distro curl wget git -y

---

2. Install Ubuntu dengan Proot-Distro

Install Ubuntu:

proot-distro install ubuntu

Masuk ke Ubuntu:

proot-distro login ubuntu

Cek versi Ubuntu:

cat /etc/os-release

Contoh output:

PRETTY_NAME="Ubuntu 24.04 LTS"

---

3. Update Ubuntu

Karena kita sudah login sebagai root, tidak perlu menggunakan sudo.

apt update && apt upgrade -y

Install package dasar:

apt install curl wget git build-essential ca-certificates -y

---

4. Install Node.js dari NodeSource

Jangan gunakan Node.js dan npm bawaan repository Ubuntu jika mengalami masalah dependency. Gunakan NodeSource.

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

5. Install 9router

Install secara global:

npm install -g 9router

Verifikasi:

9router --help

---

6. Install OpenCode

Install secara global:

npm install -g opencode-ai

Verifikasi:

opencode --help

---

7. Menyimpan Project di Storage Android

Agar project dapat diakses dari ZArchiver, Acode, VS Code Android, atau file manager lainnya, gunakan folder Documents Android.

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

8. Cara Masuk Kembali ke Ubuntu

Dari Termux:

proot-distro login ubuntu

---

9. Cara Keluar dari Ubuntu

exit

---

10. Troubleshooting

npm error atau dependency rusak

Hapus Node.js bawaan Ubuntu:

apt purge nodejs npm -y
apt autoremove -y

Kemudian ulangi langkah instalasi NodeSource.

---

Tidak bisa akses file dari ZArchiver

Gunakan folder:

/sdcard/Documents

atau

~/storage/documents

untuk menyimpan source code dan project.

Jangan memindahkan seluruh filesystem Ubuntu ke Documents karena filesystem Android tidak mendukung seluruh fitur Linux seperti symlink dan permission yang dibutuhkan Ubuntu.

---

Ringkasan Instalasi Cepat

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