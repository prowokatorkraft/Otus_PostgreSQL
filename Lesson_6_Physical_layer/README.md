# Физический уровень PostgreSQL
## Установка и настройка PostgreSQL

1. <b>Цель:</b>
    * создавать дополнительный диск для уже существующей виртуальной машины, размечать его и делать на нем файловую систему
    * переносить содержимое базы данных PostgreSQL на дополнительный диск
    * переносить содержимое БД PostgreSQL между виртуальными машинами

1. <b>Описание/Пошаговая инструкция выполнения домашнего задания:</b></br>
    * создайте виртуальную машину c Ubuntu 20.04/22.04 LTS в GCE/ЯО/Virtual Box/докере
    * поставьте на нее PostgreSQL 15 через `sudo apt`
    * проверьте что кластер запущен через `sudo -u postgres pg_lsclusters`
    * зайдите из под пользователя postgres в psql и сделайте произвольную таблицу с произвольным содержимым
        `postgres=# create table test(c1 text);
        postgres=# insert into test values('1');
        \q`
    * остановите postgres например через `sudo -u postgres pg_ctlcluster 15 main stop`
    * создайте новый диск к ВМ размером 10GB
    * добавьте свеже-созданный диск к виртуальной машине - надо зайти в режим ее редактирования и дальше выбрать пункт attach existing disk
    * проинициализируйте диск согласно инструкции и подмонтировать файловую систему, только не забывайте менять имя диска на актуальное, в вашем случае это скорее всего будет /dev/sdb - https://www.digitalocean.com/community/tutorials/how-to-partition-and-format-storage-devices-in-linux
    * перезагрузите инстанс и убедитесь, что диск остается примонтированным (если не так смотрим в сторону fstab)
    * сделайте пользователя postgres владельцем /mnt/data - `chown -R postgres:postgres /mnt/data/`
    * перенесите содержимое /var/lib/postgres/14 в /mnt/data - `mv /var/lib/postgresql/15/mnt/data`
    * попытайтесь запустить кластер - `sudo -u postgres pg_ctlcluster 15 main start`
    * <b>напишите получилось или нет и почему?</b>
      > <i>Получил ошибку `Error: /var/lib/postgresql/15/main is not accessible or does not exist`
      > потому что отсутствует директория с данными</i>
    * задание: найти конфигурационный параметр в файлах раположенных в /etc/postgresql/15/main который надо поменять и поменяйте его
    * <b>напишите что и почему поменяли</b>
      > <i>Под пользователем postgres отредактировал конфиг `nano /etc/postgresql/15/main/postgresql.conf`
      > и поменял путь директории с данными на другом диске `data_directory = '/mnt/data/main'`</i>
    * попытайтесь запустить кластер - `sudo -u postgres pg_ctlcluster 15 main start`
    * <b>напишите получилось или нет и почему</b>
      > <i>Кластер стартонул и данные отобразились</i>
    * зайдите через через psql и проверьте содержимое ранее созданной таблицы
    * задание со звездочкой *: не удаляя существующий инстанс ВМ сделайте новый, поставьте на его PostgreSQL, удалите файлы с данными из /var/lib/postgres, перемонтируйте внешний диск который сделали ранее от первой виртуальной машины ко второй и запустите PostgreSQL на второй машине так чтобы он работал с данными на внешнем диске, расскажите как вы это сделали и что в итоге получилось.
 1. <b>Результаты выполнения</b></br>
   ![Установка](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_6_Physical_layer/2023-04-23_20h12_45.png)
   ![Установка](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_6_Physical_layer/2023-04-23_20h16_50.png)
   ![Установка](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_6_Physical_layer/2023-04-23_20h21_59.png)
   ![Установка](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_6_Physical_layer/2023-04-23_20h10_20.png)
   ![Установка](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_6_Physical_layer/2023-04-23_20h25_06.png)