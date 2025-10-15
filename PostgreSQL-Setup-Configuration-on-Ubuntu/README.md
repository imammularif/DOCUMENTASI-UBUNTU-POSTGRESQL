# PostgreSQL Setup & Configuration on Ubuntu

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

note : jika ada kendala conect ke servernya, biasanya setelah install postgresql-nya, superuser/admin sudah otomatis ter create, dan biasanya mereka menggunakan password untuk conek ke conection servernya. untuk mengubah passwordnya, cukup menggunakan perintah alter :

--login dulu
```bash
 psql -u postgres -d postgres
  ```

--lalu alter password
```bash
 alter user postgres with password 'superuser12345';
  ```
   
3. Cek versi PostgreSQL:

 ```bash
 psql --version
  ```
atau 

 ```bash
 ls /etc/postgresql/
  ```

## 2. Konfigurasi PostgreSQL

1. Buka file konfigurasi:

```bash
sudo nano /etc/postgresql/<versi>/main/postgresql.conf
  ```

2. Cari baris port dan ubah sesuai kebutuhan:

```bash
port = 5433
   ```

3. Simpan dan keluar (Ctrl+X, Y, Enter).

## 3. Restart PostgreSQL

Supaya konfigurasi baru aktif:

```bash
sudo systemctl restart postgresql
   ```

## 4. Verifikasi Port
```bash
sudo netstat -plnt | grep postgres
   ```
atau menggunaka ss

```bash
sudo ss -plnt | grep postgres
   ```



Untuk koneksi ke dbeaver, dapat dilihat dokumentasinya menggunakan link berikut : [Instalasi & konfigurasi Dbeaver](https://github.com/imammularif/Cara-Install-Dbeaver-di-Ubuntu)







