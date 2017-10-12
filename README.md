# Журналы (СУБД)

Создание БД, настройка INDEX и некоторые запросы.

### Запрос выборки определенных пользователей
SELECT `u`.`NAME` FROM `users` AS u
INNER JOIN `subscriptions` AS s ON `u`.`id` = `s`.`user_id`
INNER JOIN `magasins` AS m ON `m`.`id` = `s`.`magasin_id`
	WHERE ((YEAR(CURRENT_DATE)-YEAR(`u`.`date_birth`)) - (RIGHT(CURRENT_DATE, 5) < RIGHT(`u`.`date_birth`, 5))) >= 30
	AND `m`.`NAME` = 'Мурзилка'
	AND `s`.`subscribe` = 1;
  
### Запрос выборки случайного пользователя
SELECT * FROM `users` WHERE `id` = round(1 + rand() * (SELECT count(*) FROM `users`)) LIMIT 1;
