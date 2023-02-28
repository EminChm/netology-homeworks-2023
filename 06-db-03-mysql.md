# MYSQL
# https://github.com/netology-code/virt-homeworks/tree/virt-11/06-db-03-mysql

# Задача 1

sudo docker exec -it netology-test /bin/bash
sudo docker exec netology-test mysql -u root -p test1 < /home/emin2023/sql/ test_dump.sql
docker exec -it netology-test /bin/bash
mysql -u emin -pSecret2
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-20%20%D0%B2%2021.55.33.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-20%20%D0%B2%2021.58.46.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-20%20%D0%B2%2021.53.32.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-20%20%D0%B2%2022.06.44.png)
![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-20%20%D0%B2%2022.09.15.png)


# Задача 2

CREATE USER 'test'@'localhost' IDENTIFIED WITH mysql_native_password BY 'test-pass'
  PASSWORD EXPIRE INTERVAL 180 DAY FAILED_LOGIN_ATTEMPTS 3
  ATTRIBUTE '{"last_name": "Pretty", "first_name": "James"}';


GRANT USAGE ON *.* TO 'test'@'localhost' WITH MAX_QUERIES_PER_HOUR 100;
GRANT SELECT, INSERT ON mydatabase.* TO 'test'@'localhost';
GRANT SELECT ON test_db.* TO 'test'@'localhost';
SELECT * FROM INFORMATION_SCHEMA.USER_ATTRIBUTES WHERE USER = 'test' AND HOST = 'localhost';

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-21%20%D0%B2%2000.11.20.png)

# Задача 3

USE netology_db;
SET profiling = 1;
SELECT * FROM your_table;
SHOW PROFILES;

CREATE TABLE netology_db.fun (
  id INT NOT NULL AUTO_INCREMENT,
  name VARCHAR(50) NOT NULL,
  email VARCHAR(50) NOT NULL,
  PRIMARY KEY (id)
);

SHOW CREATE TABLE netology_db.fun;

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-21%20%D0%B2%2000.37.41.png)

SELECT ENGINE FROM INFORMATION_SCHEMA.TABLES
WHERE TABLE_SCHEMA = 'netology_db' AND TABLE_NAME = 'fun';

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-21%20%D0%B2%2000.38.54.png)

SET profiling = 1;
ALTER TABLE test_db.my_table ENGINE=InnoDB;
SHOW PROFILES;

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-21%20%D0%B2%2000.42.40.png)

SET profiling = 1;
ALTER TABLE test_db.my_table ENGINE=MyISAM;
SHOW PROFILES;

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-21%20%D0%B2%2000.41.56.png)

# Задача 4

docker exec netology-test cat /etc/my.cnf
cat /etc/my.cnf
docker cp netology-test:/etc/my.cnf .
docker cp my_mysql_container:/etc/my.cnf 
docker cp my.cnf netology-test:/etc/my.cnf

![alt text](https://github.com/EminChm/netology-homeworks-2023/blob/main/%D0%A1%D0%BD%D0%B8%D0%BC%D0%BE%D0%BA%20%D1%8D%D0%BA%D1%80%D0%B0%D0%BD%D0%B0%202023-02-23%20%D0%B2%2011.01.30.png)

![alt text]()

Единственное на что ругался докер это компрессия, ее я отключил, не совсем разобрался но большую часть тз я выполнил.

