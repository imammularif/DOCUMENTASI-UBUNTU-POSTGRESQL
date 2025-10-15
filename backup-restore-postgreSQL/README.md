# backup-restore-postgreSQL

Untuk menambah pengetahuan database saya, saya mempelajari cara backup dan restore PostgreSQL dengan baik dan benar.

Dalam proses ini, saya belajar menggunakan pg_dump dan pg_restore, memahami berbagai format backup, serta menangani tantangan seperti hak akses dan kesalahan perintah.

Repo ini menjadi dokumentasi pengalaman saya dan panduan praktis bagi siapa pun yang ingin memahami backup & restore PostgreSQL secara efisien.

1. Login postgreSQLnya

```bash
sudo -i -u postgres
```

2. lakukan back up menggunakan kuery berikut menggunakan dp_dump
(pg_dump -U nama_user -d nama_database -F c -f backup_db.backup)

```bash
pg_dump -U postgres -d coba_db -F c -f backup_latihan.backup
```
atau versi sql nya :

```bash
pg_dump -U postgres -d coba_db -F p > backup_latihan.sql
```

3. setelah itu, cek filenya :

```bash
ls | grep backup
```

4. Untuk mengetahui folder aktif tersimpanya dimana, gunakan perintah pwd :
   
```bash
pwd
```

![ilustrasi](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/backup-restore-postgreSQL/Chapture/1.png)

## RESTORE

1. buka terminal
2. masuk ke administrator postgresql-nya

 ```bash
 sudo -i -u postgres psql
 ```

3. Hapus database nya terlebih dahulu (JIKA ADA), masih masuk ke psql nya.

 ```bash
 drop database coba_db;
 ```  

4. buat database

 ```bash
 create database coba_db;
 ```  

5. restore menggunakan kueri berikut.

a. Buka terminal linuxnya

b. lalu masuk administrator postgres nya

 ```bash
 sudo -i -u postgres
 ```  
c. lalu lakukan proses backup menggunakan perintah berikut(pastikan file yang ingin dibackup sudah ada) :
 ```bash
--backup pg_dump/.sql
psql -U postgres -d coba_dbmoel -f backup_latihan.sql
 ```
atau menggunakan jika nama filenya .backup
```bash
--backup pg_restore
pg_restore -U username -d nama_database backup_file.backup
 ```  
   
