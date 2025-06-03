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

```bash
select nama,gambar from mahasiswa;
```

- **Menambah 1 record pada tabel mahasiswa (Menambah 1 data mahasiswa)**
```bash
insert into mahasiswa values(
  '','Agnes','215410000','agnes@hotmail.com','Teknik Komputer','Agnes.jpg'
);
```

```bash
insert into mahasiswa values(
  '','Fitria','215410067',-> 'fitria@gmail.com','Informatika','Fitri.jpg'
);
```

- Menampilkan data dari field tertentu  
```bash
select nama from mahasiswa;
```

```bash
select nrp,nama,jurusan from mahasiswa;
```

- **Mencari data berdasarkan nrp / nim**
```bash
select * from mahasiswa where nrp='215410072';
```

- **Menampilkan isi tabel**
```bash
select * from mahasiswa;
```

- **Melakukan Edit Data / Record berdasarkan primary key (id)**
```bash
update mahasiswa set jurusan='Informatika' where id = 2;
```

Query OK, 1 row affected (0.003 sec)
Rows matched: 1 Changed: 1 Warnings: 0// Menampilkan isi table
MariaDB [phpdasar]> select * from mahasiswa;
+----+---------+-----------+----------------------+-------------+-----------+
| id | nama | nrp | email | jurusan | gambar |
+----+---------+-----------+----------------------+-------------+-----------+
| 1 | Fransis | 215410072 | fransis@example.info | Informatika | frans.jpg |
| 2 | Agnes | 215410000 | agnes@hotmail.com | Informatika | Agnes.jpg |
| 3 | Fitria | 215410067 | fitria@gmail.com | Informatika | Fitri.jpg |
+----+---------+-----------+----------------------+-------------+-----------+
3 rows in set (0.001 sec)
// Menghapus 1 Record (atau data) berdasarkan id / primary key
MariaDB [phpdasar]> delete from mahasiswa where id=1;
Query OK, 1 row affected (0.003 sec)
// Menampilkan isi table
MariaDB [phpdasar]> select * from mahasiswa;
+----+--------+-----------+-------------------+-------------+-----------+
| id | nama | nrp | email | jurusan | gambar |
+----+--------+-----------+-------------------+-------------+-----------+
| 2 | Agnes | 215410000 | agnes@hotmail.com | Informatika | Agnes.jpg |
| 3 | Fitria | 215410067 | fitria@gmail.com | Informatika | Fitri.jpg |
+----+--------+-----------+-------------------+-------------+-----------+
2 rows in set (0.000 sec)
// Menghapus table “mahasiswa”
MariaDB [phpdasar]> drop table mahasiswa;
Query OK, 0 rows affected (0.008 sec)
// Melihat (Manampilkan) tabel pada database phpdasar
MariaDB [phpdasar]> show tables;
Empty set (0.001 sec)
// Menghapus database
MariaDB [phpdasar]> drop database phpdasar;
Query OK, 0 rows affected (0.003 sec)
// Menampilkan (Melihat) database
MariaDB [(none)]> show databases;
+--------------------+
| Database |
+--------------------+
| akademik |
| db_peminjaman |
| db_pengguna |
| db_perpus |
| information_schema |
| mysql |
| performance_schema |
| phpmyadmin |
| test |+--------------------+
9 rows in set (0.002 sec)
MariaDB [(none)]>
