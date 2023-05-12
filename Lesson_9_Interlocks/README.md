# Блокировки
## Механизм блокировок
1. <b>Цель:</b>
    * понимать как работает механизм блокировок объектов и строк

1. <b>Описание/Пошаговая инструкция выполнения домашнего задания:</b></br>
    * Настройте сервер так, чтобы в журнал сообщений сбрасывалась информация о блокировках, удерживаемых более 200 миллисекунд. Воспроизведите ситуацию, при которой в журнале появятся такие сообщения.
      > ![1](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-11_16h27_39.png)</br>
      > ![2](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-11_16h33_00.png)</br>
    * Смоделируйте ситуацию обновления одной и той же строки тремя командами UPDATE в разных сеансах. Изучите возникшие блокировки в представлении pg_locks и убедитесь, что все они понятны.</br>
      <b>Пришлите список блокировок и объясните, что значит каждая.</b>
      > <i>Не понятно почему после обновления второй транзакции у первой сменился режим на ShareLock</i></br>
      > ![Транзакции](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-11_17h11_38.png)</br>
      > ![Итог до коммита](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-11_17h20_53.png)</br>
      > ![Иток после коммита](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-11_17h22_22.png)
    * Воспроизведите взаимоблокировку трех транзакций. </br>
      <b>Можно ли разобраться в ситуации постфактум, изучая журнал сообщений?</b>
      > ![Дедлок](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-12_15h06_04.png)</br>
      > ![Лог](https://github.com/prowokatorkraft/Otus_PostgreSQL/blob/main/Lesson_9_Interlocks/2023-05-12_15h16_22.png)
    * <b>Могут ли две транзакции, выполняющие единственную команду UPDATE одной и той же таблицы (без where), заблокировать друг друга?</b>
      > Думаю нет, первая транзакция заблокирует последущую. Первая транзакция с помощью Update без where заблокирует данные всей таблицы. (Можно догадаться что ответ ожидался обратный, но мой ответ нет)