                TUGAS

MEMBUAT DATABASE
MariaDB [(none)]> create database pemesan_film;
Query OK, 1 row affected (0.004 sec)
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| pemesan_film       |
| performance_schema |
| test               |
+--------------------+
5 rows in set (0.002 sec)


MENAMPILKAN DESKRIPSI TABEL
MariaDB [pemesan_film]> desc member;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| member_id | char(9)     | NO   | PRI | NULL    |       |
| full_name | varchar(30) | YES  |     | NULL    |       |
| addres    | varchar(30) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
3 rows in set (0.160 sec)


MariaDB [pemesan_film]> desc movie;
+-------------+-------------+------+-----+---------+-------+
| Field       | Type        | Null | Key | Default | Extra |
+-------------+-------------+------+-----+---------+-------+
| id_movie    | char(6)     | NO   | PRI | NULL    |       |
| member_id   | char(6)     | YES  | MUL | NULL    |       |
| movie_reted | varchar(30) | YES  |     | NULL    |       |
+-------------+-------------+------+-----+---------+-------+
3 rows in set (0.057 sec)


MENAMPILKAN ISI TABEL
MariaDB [pemesan_film]> select * from member;
+-----------+-------------+------------------------+
| member_id | full_name   | addres                 |
+-----------+-------------+------------------------+
| 01        | Janet Jones | frist street plot no 4 |
| 02        | Robert Phil | third street 34        |
| 03        | Robert Phil | fifth Avanue           |
+-----------+-------------+------------------------+
3 rows in set (0.110 sec)

MariaDB [pemesan_film]> select * from movie;
+----------+-----------+--------------------------+
| id_movie | member_id | movie_reted              |
+----------+-----------+--------------------------+
| 01       | 01        | pirates of the caribbean |
| 02       | 01        | clash of the titans      |
| 03       | 02        | forgetting sarah marshal |
| 04       | 02        | daddys little girls      |
| 05       | 03        | clash of the titans      |
+----------+-----------+--------------------------+
5 rows in set (0.001 sec)


QUERY UNTUK MENAMPILKAN NAMA DAN PESANAN 
MariaDB [pemesan_film]> select member.full_name, movie.movie_reted
    -> from movie
    -> inner join member on member.member_id = movie.member_id
    -> where full_name = 'Janet Jones';
+-------------+--------------------------+
| full_name   | movie_reted              |
+-------------+--------------------------+
| Janet Jones | pirates of the caribbean |
| Janet Jones | clash of the titans      |
+-------------+--------------------------+
2 rows in set (0.001 sec)
