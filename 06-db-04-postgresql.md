# PostgreSQL

# https://github.com/netology-code/virt-homeworks/tree/virt-code/PostgreSQL


# Задача 1

docker run --name netology2 -e POSTGRES_PASSWORD=123 -v my_dbdata:/var/lib/postgresql/data -d postgres:13
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2018.16.01.png)
docker exec -it netology2 psql -U postgres
Для вывода списка БД в psql можно использовать команду: \l
Для подключения к БД используется команда: \c dbname username
Для вывода списка таблиц в текущей БД используется команда: \dt
Для вывода описания содержимого таблицы можно использовать команду: \d+ tablename
Для выхода из psql используется команда: \q

# Задача 2

CREATE DATABASE test_database;
CREATE USER admin WITH PASSWORD '123';
docker exec -i netology2 psql -U admin -d test_database < /home/emin2023/sql/test2_dump.sql 
or i can do it inside docker by 
psql -U admin -d test_database < /home/emin2023/sql/test2_dump.sql
SELECT attname, avg_width FROM pg_stats WHERE tablename = 'orders' ORDER BY avg_width DESC LIMIT 1;
