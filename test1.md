# PostgreSQL

# https://github.com/netology-code/virt-homeworks/tree/virt-code/PostgreSQL


Задача 1

docker run --name netology2 -e POSTGRES_PASSWORD=123 -v my_dbdata:/var/lib/postgresql/data -d postgres:13
docker exec -it netology2 psql -U postgres
Для вывода списка БД в psql можно использовать команду: \l
Для подключения к БД используется команда: \c dbname username
Для вывода списка таблиц в текущей БД используется команда: \dt
Для вывода описания содержимого таблицы можно использовать команду: \d+ tablename
Для выхода из psql используется команда: \q
