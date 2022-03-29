# Дипломный проект профессии «Тестировщик»

- [Задание](https://github.com/netology-code/qa-diploma)
- [Тестовый план](https://github.com/AndryRusff/AQA_Diploma/blob/master/doc/Plan.md)

## Предварительные требования
1. На ПК должны быть установлены и настроены:
	- Git
	- Docker Desktop
	- Intellij IDEA
	
## Инструкция по запуску проекта
1. Склонировать проект на свой компьютер
	- открыть терминал в Intellij IDEA (Alt+F12)
	- ввести команду *git clone https://github.com/AndryRusff/AQA_Diploma*
2. Открыть склонированный проект 
3. Запустить Docker через терминал командой *docker-compose up -d*
4. В зависимости от выбранной БД запустить команду: 
- для MySQL: *java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar ./artifacts/aqa-shop.jar*
- для Postgre: *java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar ./artifacts/aqa-shop.jar*
5. Проверить запущенные контейнеры через терминал командой: *docker ps*
6. Убедиться, что SUT (system under test) доступен по адресу **localhost:8080**

## Для запуска тестов:
1. Запустить в отдельном терминале команду: 
- *gradlew test -Dselenide.headless=true -Durlbd=jdbc:mysql://localhost:3306/app --info* (для MySQL), 
или 
- *gradlew test -Dselenide.headless=true -Durlbd=jdbc:postgresql://localhost:5432/app --info* (для Postgre);
2. По окончании прогона тестов запустить отчет двумя последовательными командами:
- *gradlew allureReport*
- *gradlew allureServe*
3. В браузере должно появиться окно с отчётами и статистикой по тестам.

## Завершение работы и удаление контейнера:
1. Остановить контейнер Docker командой: *docker-compose down*.