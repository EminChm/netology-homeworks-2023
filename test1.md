# PostgreSQL
# https://u.netology.ru/backend/uploads/lms/attachments/files/data/49069/9._PostgreSQL.pdf
# https://github.com/netology-code/virt-homeworks/tree/virt-code/PostgreSQL

docker run --name netology2 -e POSTGRES_PASSWORD=123 -v my_dbdata:/var/lib/postgresql/data -d postgres:13
