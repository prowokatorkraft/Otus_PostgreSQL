# Виды и устройство репликации в PostgreSQL
## Репликация
1. <b>Цель:</b>
    * реализовать свой миникластер на 3 ВМ.

1. <b>Описание/Пошаговая инструкция выполнения домашнего задания:</b></br>
    * На 1 ВМ создаем таблицы test для записи, test2 для запросов на чтение.
    * Создаем публикацию таблицы test и подписываемся на публикацию таблицы test2 с ВМ №2.
    * На 2 ВМ создаем таблицы test2 для записи, test для запросов на чтение.
    * Создаем публикацию таблицы test2 и подписываемся на публикацию таблицы test1 с ВМ №1.
    * 3 ВМ использовать как реплику для чтения и бэкапов (подписаться на таблицы из ВМ №1 и №2 ).
        > Скрины выкладывать не стал, т.к. слишком много лишний действий было, но попытаюсь объяснить.
        > Создал 1 vm, поставил постгрес, открыл внешние доступы, создал таблицы, а также сделал публикацию на 1 таблицу.
        > Запуслил 2 vm, проверил доступы, создал 2 таблицы, создал публикацию 2 таблицы и подписал 1 к 1 таблице 1 vm.</br>
        > Подпсал 2 таблицу 1 vm к 2 таблице 2 vm, а затем открыл 3 vm создал 2 таблицы и подписал обе к таблицам других vm.</br>
        > сделал пару добавление со значением 1 для проверки, просле сделал еще 2 добавления и результат можем видеть на скрине.</br>
        > были проблемы с доспупами кластера при создании подписки, а также с доступами во вне, бывало пересоздавал 1 кластер.</br>
        > ![Репликация](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_14_Replication/2023-05-28_17h30_26.png)</br>
