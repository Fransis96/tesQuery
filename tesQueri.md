// Masuk ke MySQL  
```
mysql -u root
``` 

// Melihat daftar database
```
MariaDB [(none)]> show databases;
```
// Membuat database
```bash
create database phpdasar;
Query OK, 1 row affected (0.002 sec)
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
| phpdasar |
| phpmyadmin |
| test |
+--------------------+
10 rows in set (0.001 sec)
// Masuk kedalam database (Menggunakan database)
MariaDB [(none)]> use phpdasar;
Database changed// Membuat table dengan nama mahasiswa
MariaDB [phpdasar]> create table mahasiswa(
-> id int primary key auto_increment,
-> nama varchar(100),
-> nrp char(9),
-> email varchar(100),
-> jurusan varchar(100),
-> gambar varchar(100)
-> );
Query OK, 0 rows affected (0.012 sec)
// Melihat tabel-tabel di database phpdasar
MariaDB [phpdasar]> show tables;
+--------------------+
| Tables_in_phpdasar |
+--------------------+
| mahasiswa |
+--------------------+
1 row in set (0.001 sec)
// Melihat deskripsi tabel
MariaDB [phpdasar]> describe mahasiswa;
+---------+--------------+------+-----+---------+----------------+
| Field | Type | Null | Key | Default | Extra |
+---------+--------------+------+-----+---------+----------------+
| id | int(11) | NO | PRI | NULL | auto_increment |
| nama | varchar(100) | YES | | NULL | |
| nrp | char(9) | YES | | NULL | |
| email | varchar(100) | YES | | NULL | |
| jurusan | varchar(100) | YES | | NULL | |
| gambar | varchar(100) | YES | | NULL | |
+---------+--------------+------+-----+---------+----------------+
6 rows in set (0.046 sec)
// Menambahkan data kedalam tabel
MariaDB [phpdasar]> insert into mahasiswa values ('', 'Fransis', '215410072',
'fransis@example.info','Informatika','frans.jpg');
Query OK, 1 row affected, 1 warning (0.005 sec)
MariaDB [phpdasar]> select * from mahasiswa;
+----+---------+-----------+----------------------+-------------+-----------+
| id | nama | nrp | email | jurusan | gambar |
+----+---------+-----------+----------------------+-------------+-----------+
| 1 | Fransis | 215410072 | fransis@example.info | Informatika | frans.jpg |
+----+---------+-----------+----------------------+-------------+-----------+
1 row in set (0.001 sec)
// Melihat isi tabel
MariaDB [phpdasar]> select nama from mahasiswa;
+---------+
| nama |
+---------+| Fransis |
+---------+
1 row in set (0.000 sec)
// Melihat data pada field tertentu (Misalnya NIM / nrp)
MariaDB [phpdasar]> select nrp from mahasiswa;
+-----------+
| nrp |
+-----------+
| 215410072 |
+-----------+
1 row in set (0.001 sec)
MariaDB [phpdasar]> select nrp,nama from mahasiswa;
+-----------+---------+
| nrp | nama |
+-----------+---------+
| 215410072 | Fransis |
+-----------+---------+
1 row in set (0.001 sec)
MariaDB [phpdasar]> select nrp,nama,jurusan from mahasiswa;
+-----------+---------+-------------+
| nrp | nama | jurusan |
+-----------+---------+-------------+
| 215410072 | Fransis | Informatika |
+-----------+---------+-------------+
1 row in set (0.001 sec)
MariaDB [phpdasar]> select nama,gambar from mahasiswa;
+---------+-----------+
| nama | gambar |
+---------+-----------+
| Fransis | frans.jpg |
+---------+-----------+
1 row in set (0.001 sec)
// Menambah 1 record pada tabel mahasiswa (Menambah 1 data mahasiswa)
MariaDB [phpdasar]> insert into mahasiswa values(
-> '',
-> 'Agnes',
-> '215410000',
-> 'agnes@hotmail.com',
-> 'Teknik Komputer',
-> 'Agnes.jpg');
Query OK, 1 row affected, 1 warning (0.003 sec)
MariaDB [phpdasar]> insert into mahasiswa values(
-> '',
-> 'Fitria',
-> '215410067',-> 'fitria@gmail.com',
-> 'Informatika',
-> 'Fitri.jpg');
Query OK, 1 row affected, 1 warning (0.005 sec)
// Meilihat / Menampilkan data tertentu pada tabel
MariaDB [phpdasar]> select nama from mahasiswa;
+---------+
| nama |
+---------+
| Fransis |
| Agnes |
| Fitria |
+---------+
3 rows in set (0.001 sec)
MariaDB [phpdasar]> select nrp,nama,jurusan from mahasiswa;
+-----------+---------+-----------------+
| nrp | nama | jurusan |
+-----------+---------+-----------------+
| 215410072 | Fransis | Informatika |
| 215410000 | Agnes | Teknik Komputer |
| 215410067 | Fitria | Informatika |
+-----------+---------+-----------------+
3 rows in set (0.001 sec)
// Mencari data berdasarkan nrp / nim
MariaDB [phpdasar]> select * from mahasiswa where nrp='215410072';
+----+---------+-----------+----------------------+-------------+-----------+
| id | nama | nrp | email | jurusan | gambar |
+----+---------+-----------+----------------------+-------------+-----------+
| 1 | Fransis | 215410072 | fransis@example.info | Informatika | frans.jpg |
+----+---------+-----------+----------------------+-------------+-----------+
1 row in set (0.001 sec)
// Menampilkan isi tabel
MariaDB [phpdasar]> select * from mahasiswa;
+----+---------+-----------+----------------------+-----------------+-----------+
| id | nama | nrp | email | jurusan | gambar |
+----+---------+-----------+----------------------+-----------------+-----------+
| 1 | Fransis | 215410072 | fransis@example.info | Informatika | frans.jpg |
| 2 | Agnes | 215410000 | agnes@hotmail.com | Teknik Komputer | Agnes.jpg |
| 3 | Fitria | 215410067 | fitria@gmail.com | Informatika | Fitri.jpg |
+----+---------+-----------+----------------------+-----------------+-----------+
3 rows in set (0.000 sec)
// Melakukan Edit Data / Record berdasarkan primary key (id)
MariaDB [phpdasar]> update mahasiswa set jurusan='Informatika' where id = 2;
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
