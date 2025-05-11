# Домашнее задание к занятию «Работа с данными (DDL/DML)»

## Шкутов Иван Владимирович

---

## Задание 1

### 1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

### 1.2. Создайте учётную запись sys_temp.

### 1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

### 1.4. Дайте все права для пользователя sys_temp.

### 1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

### 1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос:

ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

### 1.6. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

### 1.7. Восстановите дамп в базу данных.

### 1.8. При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

---

### 1.1.

### apt-get install gnupg

Переходим на сайт https://dev.mysql.com и выбераем пакет для установки mysql:

### mysql --version

Установим MySQL сервер:

### apt-get install mysql-server 


![1](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/1.jpg).

![2](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/2.jpg).


### 1.2.

Заходим в консоль базы данных под root:

### mysql -u root -p

Создаем учётную запись sys_temp:

### CREATE USER 'sys_temp'@'localhost' IDENTIFIED BY 'password'; 

![3](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/3.jpg).


### 1.3.

Выполняем запрос на получение списка пользователей в базе данных:

### SELECT user FROM mysql.user;

![4](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/4.jpg).


### 1.4.

Даем все права для пользователя sys_temp:

### GRANT ALL PRIVILEGES ON * . * TO ‘sys_temp’@’localhost’ WITH GRANT OPTION;



### 1.5.

Выполните запрос на получение списка прав для пользователя sys_temp:

### SHOW GRANTS FOR 'sys_temp'@'localhhost';

![5](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/5.jpg).


### 1.6.

Переподключиться к базе данных от имени sys_temp. Для смены типа аутентификации с sha2 указываем:

### ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

Проверяем всех пользователей, котрые могут подключиться к базе:

### SELECT user,host from mysql.user;

Выполняем запрос от какого пользователя сейчас идет сеанс работы с базой:

### SELECT CURRENT_USER();

![6](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/6.jpg).


### 1.6.

По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачиваем дамп базы данных:

### wget https://downloads.mysql.com/docs/sakila-db.zip

![7](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/7.jpg).


### 1.7.

Восстанавливаем дампы в базу данных:

### source /home/Downloads/sakila-db/sakila-schema.sql

### source /home/Downloads/sakila-db/sakila-data.sql


### 1.8.

Выводим в командной строке все загруженные таблицы из базы данных:

### SHOW FULL TABLES;

Устанавливаем DBeaver и в IDE формируем ER-диаграмму получившейся базы данных:

### apt policy dbeaver-ce

Выбераем необходимую базу данных из списка. В нашем случае MySQL и выводим диаграммы скаченной базы данных:

### sakila

### sys

![8](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/8.jpg).

![9](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/9.jpg).

![10](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/10.jpg).

![11](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/11.jpg).

![12](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/12.jpg).

![13](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/13.jpg).

![14](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/14.jpg).

![15](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/15.jpg).


---

## Задание 2

### Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)

Название таблицы | Название первичного ключа

customer         | customer_id

---

![16](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/16.jpg).

![17](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/17.jpg).

![19](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/19.png).

---

## Дополнительные задания (со звёздочкой*)

Эти задания дополнительные, то есть не обязательные к выполнению, и никак не повлияют на получение вами зачёта по этому домашнему заданию. Вы можете их выполнить, если хотите глубже шире разобраться в материале.

## Задание 3*

### 3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

### 3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.

---


![31](https://github.com/Ivan-Shkutov/sdb-homeworks-12-02/blob/main/img/31.png).


### mysql> REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'sys_temp'@'localhost';

### mysql> SHOW GRANTS FOR 'sys_temp'@'localhost';

### mysql> GRANT INSERT, UPDATE, DELETE ON ` sakila `.* TO 'sys_temp'@'localhost';

### mysql> SHOW GRANTS FOR 'sys_temp'@'localhost';

### mysql> REVOKE INSERT, UPDATE, DELETE ON ` sakila `.* FROM 'sys_temp'@'localhost';

### mysql> SHOW GRANTS FOR 'sys_temp'@'localhost';


Команда GRANT предоставляет пользователям или ролям определённые привилегии на объекты базы данных.

Команда REVOKE отзывает ранее предоставленные привилегии у пользователей или ролей.

### Синтаксис предоставления привилегий для таблицы в MySQL:

GRANT privileges ON object TO user;

### Синтаксис отмены привилегий на таблицу в MySQL:

REVOKE privileges ON object FROM user;

---

