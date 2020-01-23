# Бот телеграмм для слежки за доменами.

Приложение парсит домены и ssl сертификаты, и привязывает их к пользователю, потом сигнализирует о их окончании.

Приложение использует PROXY, так как у меня РКН (роском надзор) блокирует TELEGRAM

`sudo apt-get install tor`

### Нужно зарегистрировать бота.

Идем к TheBotFather и регистрируем webhook, САЙТ ДОЛЖЕН БЫТЬ ДОСТУПЕН ПО https c SSL.

https://api.telegram.org/bot~TOKEN~/setWebhook?url="url/bot"


### Заполняем settings.php

Переименовываем settings.example.php -> settings.php

Создаем новую бд и прописываем все доступы к ней в settings.php

Заполняем TOKEN

### Восстанавливаем дамп.

Для корректной работы приложения нужно восстановить дамп из файла start.sql

`mysql -u username -p databases<start.sql`

username - Имя пользователя

databases - Название базы данных

### Доступные команды.

`/start` - Начальная страница

`/help`	- Вывести все команды

`/addDomain имя_домена`	- Привязать домен

`/destroyDomain имя_домена`	- Удалить домен

`/allDomains` - Вывести все домены

### Автоматические уведомления.

Для автоматических уведомлений необходимо добавить crontab

`crontab -e`

`0 12 * * * wget url/check`
