Создать проект с двумя модулями (maven) и общим родителем.
Версии зависимостей должны быть указаны только в родителе.

Модуль 1:
Библиотека-стартер на основе Spring Boot автоконфигураций, делающая так, что все вызовы публичных методов компонентов,
отмеченных Spring-аннотацией @Service, будут логироваться сообщением "{methodName} args: [{args}]" (например: "saveFile
args: [ "order.pdf", 123, "application/pdf"]").
Должна быть возможность отключить автоконфигурацию библиотеки через spring-property "libname.enabled", либо
автоконфигурация не срабатывает при отсутствии spring-aop классов. Реализовать возможность не логировать определённые
аргументы (например большой массив байт логировать вредно, пароли логировать вредно). Имя логгера должно соответствовать
имени класса сервиса.
Должны быть тесты на автоконфигурацию.

Модуль 2:
Должен использовать библиотеку сделанную в модуле 1. Реализовать web приложение при помощи Spring Boot, с двумя
REST-методами - сохранить файл, получить файл. Хранение файла должно быть БД (можно выбрать любую БД). Размер файла - не
более 1 мб. При получении файла должен возвращаться оригинальный Content-Type и правильный Content-Disposition с
оригинальным именем файла.
Должны быть интеграционные @SpringBootTest тесты на REST-методы с использованием mockMvc и тестовой БД через
testcontainers.