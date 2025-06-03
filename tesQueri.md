- **Masuk ke MySQL**
```
mysql -u root
``` 

- **Melihat daftar database**
```
MariaDB [(none)]> show databases;
```
- **Membuat database**
```bash
create database phpdasar;
```  
- **Masuk kedalam database** (*Menggunakan database*)
```bash
use phpdasar;
```
- **Membuat table dengan nama mahasiswa**
```bash  
create table mahasiswa(
  id int primary key auto_increment,
  nama varchar(100),
  nrp char(9),
  email varchar(100),
  jurusan varchar(100),
  gambar varchar(100)
);
```

- **Melihat tabel-tabel di database phpdasar**
```bash
show tables;
```

- **Melihat deskripsi tabel**
```bash
describe mahasiswa;
```

- **Menambahkan data kedalam tabel**
```bash
insert into mahasiswa values (
  '', 'Fransis', '215410072', 'fransis@example.info','Informatika','frans.jpg'
);
``` 

- **Melihat isi tabel**
```bash
select * from mahasiswa;
```

- **Menampilkan data dari field nama**
```bash
select nama from mahasiswa;
```

- **Melihat data pada field tertentu (Misalnya NIM / nrp)**
```bash
select nrp from mahasiswa;
```

```bash
select nrp,nama from mahasiswa;
```

```bash
select nrp,nama,jurusan from mahasiswa;
```
- **READ**
```bash
select nama,gambar from mahasiswa;
```

- **Menambah 1 record pada tabel mahasiswa (CREATE)**
```bash
insert into mahasiswa values(
  '','Agnes','215410000','agnes@hotmail.com','Teknik Komputer','Agnes.jpg'
);
```

- **Menampilkan data dari field tertentu  (READ)**
```bash
select nama from mahasiswa;
```
- **READ**
```bash
select nrp,nama,jurusan from mahasiswa;
```

- **Mencari data berdasarkan nrp / nim (READ - SEARCHING)**
```bash
select * from mahasiswa where nrp='215410072';
```

- **Menampilkan isi tabel**
```bash
select * from mahasiswa;
```

- **Melakukan Edit Data / Record berdasarkan primary key "id" (UPDATE)**
```bash
update mahasiswa set jurusan='Informatika' where id = 2;
```

- **Menampilkan isi table (READ)**
```bash
select * from mahasiswa;
```

- **Menghapus 1 Record (atau data) berdasarkan id / primary key**
```bash
delete from mahasiswa where id=1;
```

- **Menampilkan isi table (READ)**
```bash
select * from mahasiswa;
```
- **DELETE**
```bash
delete from mahasiswa where id=1;
```

- **Menghapus table “mahasiswa”**
```bash
drop table mahasiswa;
``` 

- **Menghapus database**
```bash
drop database phpdasar;
```

- **Menampilkan (Melihat) database**
```bash
show databases;
```

---
### LAINNYA

```bash
create database toko;
```
```bash
use toko;
```
```bash
create table if not exists barang (
  id int auto_increment not null primary key,
  nama varchar(40) not null,
  harga int not null default 0,
  stok int not null default 0,
  foto varchar(70) not null default ''
);
```
```bash
insert into barang(nama,harga,stok, foto) values
  ('Sepatu Adidas 1',500000,5,'sepatu1.jpg'),
  ('Sepatu Adidas 2',600000,5,'sepatu2.jpg'),
  ('Sepatu Converse 1',450000,6,'sepatu3.jpg'),
  ('Sepatu Converse 2',550000,6,'sepatu4.jpg'),
  ('Sepatu Sneakers 1',560000,7,'sepatu5.jpg'),
  ('Sepatu Sneakers 2',660000,7,'sepatu6.jpg'),
  ('Sepatu Sneakers 3',760000,4,'sepatu7.jpg');
```
