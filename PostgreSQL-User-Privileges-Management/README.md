## User Privileges Management in PostgreSQL (CRUD access control)

Di pekerjaan sebelumnya sebagai technical support yang berperan penting dalam memanajement/validasi data untuk user internal di sebuah perusahaan menggunakan kuery sql, saya mempelajari & menyadari bahwa pentingnya pengaturan hak akses user di database. Dari situ saya mulai & berinisiatif mendalami bagaimana cara membuat, mengatur, dan memberikan hak akses CRUD di PostgreSQL secara aman dan efisien. Mini-Project/dasar pengetahuan yang saya miliki ini menjadi bagian dari proses saya memahami/mensimulasikan manajemen keamanan data serta memperkuat dasar pengetahuan saya di bidang database administration dan data governance. #semoga bermanfaat :)

### 1. Membuat User baru

--masuk ke administrator postgresql-nya
```bash 
sudo -i -u postgres
```

```bash 
psql
```

-- membuat user baru

```bash 
CREATE USER imul_crud WITH PASSWORD 'supersecret123';
```

### 2. Membuat Database

```bash 
CREATE DATABASE db_test OWNER imul_crud;
```
atau jika databasenya sudah ada, konek usernya ke database-nya (ini wajib dilakukan ketika membuat user baru dan koneksikan ke database yang dituju)

```bash 
GRANT CONNECT ON DATABASE db_test TO imul_crud;
```

### 3. Memberikan/buat Hak Akses-nya


```bash 
GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO imul_crud;
```
atau beri hak user select 
```bash 
GRANT SELECT ON ALL TABLES IN SCHEMA public TO nama_user;
```
atau select & update
```bash 
GRANT SELECT, UPDATE ON ALL TABLES IN SCHEMA public TO nama_user;
```
lalu
```bash 
GRANT CREATE ON SCHEMA public TO imul_crud;
```

-- Hak CRUD untuk tabel baru (default privileges)/ini jika ada pembuatan table baru dari superuser dan beri permission ke semua user/user yang dituju

(contoh untuk user dengan hak akses crud(SELECT, INSERT, UPDATE, DELETE)
```bash 
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT SELECT, INSERT, UPDATE, DELETE ON TABLES TO imul_crud;
```

### 4. Cek User & Hak Akses (Optional)

-- Daftar semua user / role

```bash 
\du
```
![cek users](https://github.com/imammularif/PostgreSQL-User-Privileges-Management/blob/main/Chapture/cek%20user.png)

-- kueri untuk cek daftar user dan hak aksesnya menggunakan sql script (jika cek menggunakan user superuser, semua user dan hak aksesnya akan di tampilin semua)

```bash 
SELECT grantee AS "User",
       table_schema AS "Schema",
       table_name AS "Table",
       string_agg(privilege_type, ', ') AS "Privileges"
FROM information_schema.role_table_grants
GROUP BY grantee, table_schema, table_name
ORDER BY grantee, table_schema, table_name;
```
(ilustrasi ini saya cek menggunakan user imul_crud)
![cek hak akses users](https://github.com/imammularif/PostgreSQL-User-Privileges-Management/blob/main/Chapture/Screenshot%202025-10-09%20204010.png)

NOTE : Project ini saya buat sebagai latihan dan dokumentasi pribadi untuk memperdalam pemahaman tentang pengelolaan hak akses user di PostgreSQL secara praktis.




