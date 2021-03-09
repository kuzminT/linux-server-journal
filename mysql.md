## Convert character set

	ALTER TABLE `db`.`table` CONVERT TO CHARACTER SET cp1251 COLLATE cp1251_general_ci;

**SHOW DATABASE SIZE**

	SELECT pg_size_pretty( pg_database_size('db_name') );


