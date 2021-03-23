## Sequences
You can see the sequences in your database using the `\ds` command in psql. Update sequence:

`ALTER SEQUENCE product_id_seq RESTART WITH 1453`

## Postgres

- [15 полезных команд PostgreSQL](https://tproger.ru/translations/useful-postgresql-commands/)
- [How To Move a PostgreSQL Data Directory to a New Location on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-move-a-postgresql-data-directory-to-a-new-location-on-ubuntu-18-04)


## Import large data

- [Populating a Database](https://www.postgresql.org/docs/current/populate.html) - optimizations for large import.


## Bulk operations with large data

- [PostgreSQL: How to update large tables](https://blog.codacy.com/how-to-update-large-tables-in-postgresql/)

## JSONB

- [Faster Operations with the JSONB Data Type in PostgreSQL](https://www.compose.com/articles/faster-operations-with-the-jsonb-data-type-in-postgresql/)
- [When To Avoid JSONB In A PostgreSQL Schema](https://heap.io/blog/engineering/when-to-avoid-jsonb-in-a-postgresql-schema)

## Control access

- [PostgreSQL - How to grant access to users?](https://tableplus.com/blog/2018/04/postgresql-how-to-grant-access-to-users.html)

## Pgbouncer

- [Настраиваем пул соединений к PostgreSQL с PgBouncer](https://eax.me/pgbouncer/)

## Backups

- [Как не потерять данные в PostgreSQL](https://habr.com/ru/post/197742/) - регулярные дампы файлового каталога через `pg_basebackup`.
- [Automated Backup on Linux](https://wiki.postgresql.org/wiki/Automated_Backup_on_Linux)

## Сбор статистики

- [Сборщик статистики](https://postgrespro.ru/docs/postgrespro/9.5/monitoring-stats)

    
        # Show statistics of all tables in db:
        select relname, n_live_tup from pg_stat_user_tables;

- [Как одно изменение конфигурации PostgreSQL улучшило производительность медленных запросов в 50 раз](https://infostart.ru/1c/articles/1023353/)

## Replications

- [Потоковая репликация в PostgreSQL](https://prudnitskiy.pro/2018/01/05/pgsql-replica/)

## Sizes

    # Show database size:
    SELECT pg_database_size(current_database());
    SELECT pg_database_size('my_database');
    SELECT pg_size_pretty(pg_database_size(current_database()));

    # Show size of table
    SELECT pg_relation_size('accounts');
    SELECT pg_size_pretty(pg_total_relation_size('accounts'));

    # Show size of table indexes
    SELECT pg_size_pretty (pg_indexes_size('actor'));

## Optimization

- [MVCC-6. Очистка](https://habr.com/ru/company/postgrespro/blog/452320/) - Vacuum, article by Postgres Professional.
- [PostgreSQL. Хочешь похудеть? Cпроси меня как](https://postgres.men/database/postgresql/devops-usage-disks/) - оптимизация базы postgres.


Select index stat information

        SELECT schemaname, relname, indexrelname, idx_scan,
               pg_size_pretty(pg_relation_size(indexrelid)) AS idx_size
        FROM   
               pg_stat_user_indexes;


        SELECT indexrelname,
               cast(idx_tup_read AS numeric) / idx_scan AS avg_tuples,
               idx_scan,idx_tup_read 
        FROM pg_stat_user_indexes 
               WHERE idx_scan > 0;


## Monitor activity of the queries


    select * from pg_stat_activity where state = 'active';
    // polite way to stop
    SELECT pg_cancel_backend(PID);
    //stop at all costs - can lead to full database restart
    SELECT pg_terminate_backend(PID);


## Fast delete

Для быстрого удаления больших объёмов данных в таблицах с fk зайти под суперпользователем и сделать: 
    
    SET session_replication_role = replica;

Удалить нужные строки, затем вернуть констрейнты:

    SET session_replication_role = default;

Удобство в том, что работает только для сессии самого пользователя, а не для всех.

## Show schemas

    SELECT schema_name FROM information_schema.schemata

    SELECT nspname FROM pg_catalog.pg_namespace;

## Export into csv

    \copy (SELECT * FROM persons) to 'C:\tmp\persons_client.csv' with csv;

    # variant for superuser:
    COPY persons(first_name,last_name,email) TO 'C:\tmp\persons_partial_db.csv' DELIMITER ',' CSV HEADER;

## Postgres database structure

        # Show core data directory of the postgres.
        SHOW data_directory;

        # Show directory names for databases
        select oid, datname from pg_database;




