Berikut saya mendokumentasi beberapa cara sederhana untuk membuat table serta insert data kedalam database di postgreSQL

1. Buka dbeaver yang sudah di install [Cara Instalasi DBeaver](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/tree/main/Cara-Install-Dbeaver-di-Ubuntu)
2. buat koneksi baru dan login menggunakan user_crud yang sudah dibuat sebelumnya / kalau gk ngerti caranya, gunakan user default-nya saja yang sudah di-[ALTER](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/tree/main/PostgreSQL-Setup-Configuration-on-Ubuntu#1-instalasi-postgresql) passwordnya saat instalasi postgres-nya. hehehe
3. buka editor sql nya, dan buat database nya.

```bash 
create database coba_db;
```
untuk cek apakah databasenya sudah dibuat atau belum, dapat menggunakan shortcut berikut(jika menggunakan terminal(psql)) :

```bash 
\l
```
atau

```bash 
\list
```
 ![Show db](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/db.png)

4. selanjutnya, buat tabel di editor sql-nya. saya disini hanya membuat 2 table saja.

```bash
-- table customers
CREATE TABLE customers (
    id VARCHAR(10) PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(50)
);
```
-- table orders
```
CREATE TABLE orders (
    id VARCHAR(10) PRIMARY KEY,
    customer_id VARCHAR(10) REFERENCES customers(id),
    amount VARCHAR(20)
);
```
cek table yang sudah buat :
(conect dbnya dulu)
```bash
\c coba_db
```
```bash
\dt
```
 ![show table](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/table.png)
 
5. setelah buat table, lakukan insert

```bash
-- table customers
INSERT INTO customers (id, name, email) VALUES ('C001', 'Alice', '123@email.com');
```

```bash
-- table orders
INSERT INTO orders (id, customer_id, order_date, amount) VALUES ('O001', 'C001','10/09/2025' '100');
```

6. setelah membuat database, table dan insert datanya, lakukan CRUD datanya (SELECT, INSERT, UPDATE, DAN DELETE)
   
- Menampilkan data pada table customers

```bash
select * from customers;
```
  
- menampilkan data pada table orders

```bash
select * from orders;
```
  
- menampilkan kedua data/menggabungkan kedua table (left join, right join, inner join) saat ini saya menggunakan inner join saja.

```bash
select * from customers inner join orders on customers.id = orders.id;
```
 ![join](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/inner.png)

 - insert 1 data pada table customers

 ```bash
 INSERT INTO customers (id, name, email) VALUES ('C002', 'Tony', 'Tony@stark.com');
 ```

 - update 1 data table orders. di kolom order_date dari 10/9/2025 menjadi 01/01/2026

  ```bash
 update orders set order_date = '01/01/2026' where id = 'o001';
 ```
--sebelum

 ![sebelum](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/update%201.png)

 --sesudah
 ![sesudah](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/update%202.png)
   
- Delete 1 data pada table customers yang nama customersnya Alice.

 ```bash
 delete from customers where name = 'Alice';
 ```
--sebelum

![sebelum](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/del%201.png)

 --sesudah
![sesudah](https://github.com/imammularif/DOCUMENTASI-UBUNTU-POSTGRESQL/blob/main/SimpleCRUD-PostgreSQL/Chapture/del%202.png)

Terkait query CRUD sederhana yang dapat di ilustrasikan tersebut, dapat dipelajari secara lengkap fungsi dan metodenya dari sql postgressnya di [Belajar postgreSQL](https://www.w3schools.com/postgresql/index.php)
atau bisa di cari platform lain seperti youtube atau sumber online lainya, tks.

#TentunyaAuthorJugaMasihBelajar 
#DataAnalyst
