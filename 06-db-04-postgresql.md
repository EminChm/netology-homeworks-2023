# PostgreSQL

# https://github.com/netology-code/virt-homeworks/tree/virt-code/PostgreSQL


# Задача 1

docker run --name netology2 -e POSTGRES_PASSWORD=123 -v my_dbdata:/var/lib/postgresql/data -d postgres:13
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2018.16.01.png)
docker exec -it netology2 psql -U postgres
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2018.16.16.png)
Для вывода списка БД в psql можно использовать команду: \l
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2018.18.12.png)
Для подключения к БД используется команда: \c dbname username
Для вывода списка таблиц в текущей БД используется команда: \dt
Для вывода описания содержимого таблицы можно использовать команду: \d+ tablename
Для выхода из psql используется команда: \q

# Задача 2

CREATE DATABASE test_database;
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2018.47.48.png)
CREATE USER admin WITH PASSWORD '123';
docker exec -i netology2 psql -U admin -d test_database < /home/emin2023/sql/test2_dump.sql 
or i can do it inside docker by 
psql -U admin -d test_database < /home/emin2023/sql/test2_dump.sql
SELECT attname, avg_width FROM pg_stats WHERE tablename = 'orders' ORDER BY avg_width DESC LIMIT 1;
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2019.36.28.png)

# Задача 3

Создаем первую таблицу orders_1 и копируем в нее данные из исходной таблицы по условию price>499
CREATE TABLE orders_1 AS SELECT * FROM orders WHERE price>499;

Создаем вторую таблицу orders_2 и копируем в нее данные из исходной таблицы по условию price<=499
CREATE TABLE orders_2 AS SELECT * FROM orders WHERE price<=499;

Удаляем исходную таблицу orders
DROP TABLE orders;

COMMIT;
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2019.44.37.png)

При проектировании таблицы orders можно использовать горизонтальное шардирование (partitioning), при котором таблица физически разбивается на несколько разделов (partition) по заданному критерию. В этом случае данные автоматически будут распределены между разделами, что позволит избежать необходимости "ручного" разбиения таблицы в будущем.

# Задача 4

pg_dump -U postgres -d test_database -f test_database_backup.sql

ALTER USER postgres PASSWORD '123';

sudo -u postgres psql -c "ALTER USER postgres PASSWORD '123';"

что только не делал, получаю ошибку аутентификации(((

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2020.27.46.png)

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2020.27.59.png)

psql -U postgres -d test_database -c "pg_dump -U postgres -d test_database -f test_database_backup.sql"

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-26%20%D0%B2%2020.32.52.png)

ОГРОМНАЯ ПРОСЬБА ПОМОЧЬ С 4 ЫМ ЗАДАНИЕМ!
