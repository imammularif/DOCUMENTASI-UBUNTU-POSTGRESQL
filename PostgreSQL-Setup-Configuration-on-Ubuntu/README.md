# PostgreSQL Instalation/Setup & Configuration on Ubuntu

Dokumentasi ini menjelaskan cara instalasi, konfigurasi, dan pengaturan port PostgreSQL di Ubuntu. 
Dokumentasi ini dibuat sebagai referensi pribadi atau mini project.

## 1. Instalasi PostgreSQL

1. Update repository:

  ```bash
  sudo apt update
  ```

2. Install PostgreSQL:

 ```bash
 sudo apt install postgresql postgresql-contrib
  ```

Setelah postgres nya udah ke install, cek usernya :
```bash
--cooming soon--
  ```
atau, langsung alter passwornd user dafauldnya. user : postgres

--login dulu
```bash
 psql -u postgres -d postgres
  ```

--lalu alter password (alter user <nama_user> with password <'isi_password'>;)
```bash
 alter user postgres with password 'superuser12345';
  ```
note : ini berguna untuk login ke servernya menggunakan DBeaver.(pastikan portnya udah bener)
   
3. Cek versi PostgreSQL (OPTIONAL):

 ```bash
 psql --version
  ```
atau 

 ```bash
 ls /etc/postgresql/
  ```

## 2. Konfigurasi PostgreSQL (Optional)

1. Buka file konfigurasi:

```bash
sudo nano /etc/postgresql/<versi>/main/postgresql.conf
  ```

2. Cari baris port dan ubah sesuai kebutuhan:

```bash
port = 5433
   ```

3. Simpan dan keluar (Ctrl+X, Y, Enter).

## 3. Restart PostgreSQL (Optional jika ada perubahan konfigurasi Postgres-nya)

Supaya konfigurasi baru aktif:

```bash
sudo systemctl restart postgresql
   ```

## 4. Verifikasi Port / cek PORT
```bash
sudo netstat -plnt | grep postgres
   ```
atau menggunaka ss

```bash
sudo ss -plnt | grep postgres
   ```
![cek_port](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/PostgreSQL-Setup-Configuration-on-Ubuntu/Chapture/cek_port.png)

(posisi portnya ada di angka 5488 (port defauldnya : 5432) itu psosisinya udah di ubah,,wkwk

--entah kenapa saat dilakukan menggunakan fungsi netstat nya dia gk bisa, mungkin belum di inisiasi/install ke systemnya/os nya. hehe



Untuk langkah selanjutnya untuk koneksi ke dbeaver-nya, dapat dilihat dokumentasinya menggunakan link berikut : [Instalasi & konfigurasi Dbeaver](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/tree/main/Cara-Install-Dbeaver-di-Ubuntu)







