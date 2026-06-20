# Instalasi Ubuntu Proot + Node.js + 9router + OpenCode di Termux

Panduan lengkap untuk menjalankan **Ubuntu Proot**, **Node.js**, **9router**, dan **OpenCode** di Android menggunakan Termux.

---

## Prasyarat

| Kebutuhan | Keterangan |
|-----------|------------|
| Termux | Versi terbaru dari [F-Droid](https://f-droid.org/en/packages/com.termux/) |
| Internet | Koneksi stabil |
| Storage | Minimal 5 GB ruang kosong |

---

## 1. Persiapan Termux

Update package Termux:

```bash
pkg update && pkg upgrade -y
```

Install package yang dibutuhkan:

```bash
pkg install proot-distro curl wget git -y
```

---

## 2. Install Ubuntu dengan Proot-Distro

Install Ubuntu:

```bash
proot-distro install ubuntu
```

Masuk ke Ubuntu:

```bash
proot-distro login ubuntu
```

Cek versi Ubuntu:

```bash
cat /etc/os-release
```

Contoh output:

```
PRETTY_NAME="Ubuntu 24.04 LTS"
```

---

## 3. Update Ubuntu

> Karena kita sudah login sebagai **root**, tidak perlu menggunakan `sudo`.

Update package Ubuntu:

```bash
apt update && apt upgrade -y
```

Install package dasar:

```bash
apt install curl wget git build-essential ca-certificates -y
```

---

## 4. Install Node.js dari NodeSource

> **Disarankan** menggunakan Node.js dari NodeSource agar terhindar dari masalah dependency pada paket bawaan Ubuntu.

Tambahkan repository NodeSource:

```bash
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
```

Install Node.js:

```bash
apt install nodejs -y
```

Verifikasi instalasi:

```bash
node -v
npm -v
```

Contoh output:

```
v22.x.x
10.x.x
```

---

## 5. Install 9router

Install secara global:

```bash
npm install -g 9router
```

Verifikasi:

```bash
9router --help
```

---

## 6. Install OpenCode

Install secara global:

```bash
npm install -g opencode-ai
```

Verifikasi:

```bash
opencode --help
```

---

## 7. Menyimpan Project di Storage Android

Agar project dapat diakses dari aplikasi Android seperti:

- ZArchiver
- Acode
- VS Code Android
- File Manager Android

gunakan folder **Documents** Android.

```bash
cd /sdcard/Documents
mkdir project
cd project
```

Clone repository:

```bash
git clone <url-repository>
```

Contoh:

```bash
git clone https://github.com/user/repo.git
```

---

## 8. Cara Masuk Kembali ke Ubuntu

Dari Termux:

```bash
proot-distro login ubuntu
```

---

## 9. Cara Keluar dari Ubuntu

```bash
exit
```

---

## Troubleshooting

### npm Error atau Dependency Rusak

Hapus Node.js bawaan Ubuntu:

```bash
apt purge nodejs npm -y
apt autoremove -y
```

Kemudian ulangi langkah instalasi NodeSource ([Langkah 4](#4-install-nodejs-dari-nodesource)).

---

### Tidak Bisa Akses File dari ZArchiver

Gunakan salah satu lokasi berikut untuk menyimpan source code dan project:

```
/sdcard/Documents
```

atau

```
~/storage/documents
```

> **Jangan** memindahkan seluruh filesystem Ubuntu ke Documents.
> Filesystem Android tidak mendukung seluruh fitur Linux seperti:
> - Symbolic Link (symlink)
> - Permission Linux
> - Device Files
>
> yang dibutuhkan oleh Ubuntu Proot.

---

## Ringkasan Instalasi Cepat

```bash
# -- Termux --
pkg update && pkg upgrade -y
pkg install proot-distro curl wget git -y

# -- Install & Login Ubuntu --
proot-distro install ubuntu
proot-distro login ubuntu

# -- Di dalam Ubuntu --
apt update && apt upgrade -y
apt install curl wget git build-essential ca-certificates -y

# -- Install Node.js --
curl -fsSL https://deb.nodesource.com/setup_22.x | bash -
apt install nodejs -y

# -- Install Tools --
npm install -g 9router
npm install -g opencode-ai
```

---

## Selesai

Sekarang Ubuntu Proot telah siap digunakan dengan:

- **Ubuntu Proot**
- **Node.js** & **npm**
- **9router**
- **OpenCode**

Selamat ngoding di Android!
