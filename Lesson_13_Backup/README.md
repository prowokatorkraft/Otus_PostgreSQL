# Резервное копирование и восстановление
## Бэкапы
1. <b>Цель:</b>
    * Применить логический бэкап. Восстановиться из бэкапа

1. <b>Описание/Пошаговая инструкция выполнения домашнего задания:</b></br>
    * Создаем ВМ/докер c ПГ.
    * Создаем БД, схему и в ней таблицу.
    * Заполним таблицы автосгенерированными 100 записями.
    * Под линукс пользователем Postgres создадим каталог для бэкапов
    * Сделаем логический бэкап используя утилиту COPY
    * Восстановим в 2 таблицу данные из бэкапа.
    * Используя утилиту pg_dump создадим бэкап с оглавлением в кастомном сжатом формате 2 таблиц
    * Используя утилиту pg_restore восстановим в новую БД только вторую таблицу!
    * ДЗ сдается в виде миниотчета на гитхабе с описанием шагов и с какими проблемами столкнулись.
        > ![copy](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_13_Backup/2023-05-24_22h32_24.png)</br>
        > ![pg_dump_](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_13_Backup/2023-05-24_23h02_15.png)</br>