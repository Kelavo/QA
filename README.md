# Дипломный проект профессии «Тестировщик ПО»

## Описание приложения

Приложение "Путешествие дня" - это веб-сервис, который предлагает купить тур по определённой цене двумя способами:

* Обычная оплата по дебетовой карте
* Уникальная технология: выдача кредита по данным банковской карты

Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

* сервису платежей (далее - Payment Gate)
* кредитному сервису (далее - Credit Gate)

Приложение должно в собственной СУБД сохранять информацию о том, каким способом был совершён платёж и успешно ли он был
совершён (при этом данные карт сохранять не допускается).

## Документация

* [План автоматизации](https://github.com/Kelavo/QA_Diploma/blob/main/documentation/Plan.md)
* [Отчет по итогам тестирования](https://github.com/Kelavo/QA_Diploma/blob/main/documentation/Report.md)
* [Отчет по итогам автоматизации](https://github.com/Kelavo/QA_Diploma/blob/main/documentation/Summary.md)

## Инструкция для запуска автотестов:

1. Скачать проект с удаленного репозитория на свой локальный при помощи команды `git clone`;
2. Открыть проект в IDEA;
3. Запустить Docker Desktop;
4. Развернуть контейнеры MySql, PostgreSQL и Node.js в терминале IDEA с помощью команды `docker-compose up`
5. Запуск SUT. Открыть новую вкладку в терминале IDEA и ввести команду:

* **с поддержкой MySQL:**

`java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app_db" -jar artifacts/aqa-shop.jar`

* **с поддержкой PostgreSQL:**

`java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/db" -jar artifacts/aqa-shop.jar`

Убедиться, что приложение доступно по адресу: `http://localhost:8080/`

6. Запуск тестов. Открыть новую вкладку в терминале IDEA и ввести команду:

* **Для MySQL:** `.\gradlew "-Ddb.url=jdbc:mysql://localhost:3306/app_db" clean test`
* **Для PostgreSQL:** `.\gradlew "-Ddb.url=jdbc:postgresql://localhost:5432/db" clean test`

7. Генерируем отчет Allure по итогам тестирования.

Используем команду для автоматического открытия отчета: `.\gradlew allureServe`

После просмотра отчета останавливаем действие allureServe комбинацией клавиш Ctrl + C.
