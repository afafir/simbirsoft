#  Тестовое задание SimbirSoft(Backend)

Консольное приложение, которое скачивает веб-страницу на жесткий диск и выводит количество уникальных слов в консоль. Также можно сохранить эти слова в виде txt-файла или в базу данных.

## Запуск
Задание отправлено в виде архива. Папка code содержит проект(с исходным кодом), который можно открыть в IDEA. Папка program содержит исполняемый jar-архив task.jar и txt-файл с двумя сайтами для примера. Программу можно запустить в двух режимах: для записи в бд и для записи в файл. Обе реализации является декоратором над базовым счетчиком слов, выводящего слова в консоль. 
### Параметры запуска
Программа требует два аргумента для запуска: 
* Сайт, для которого считается количество слов
* Способ реализации

```bash
java -jar task.jar https://simbirsoft.com db
OR
java -jar task.jar https://simbirsoft.com file
```

### Реализация file
Программа создаст две папки( в том месте, где лежит jar-архив). В папке PAGES будут храниться скачанные HTML-страницы, в папке COUNTS будут храниться txt-файлы. Также программа напишет в консоль, куда сохранились эти файлы. 
### Реализация db
Для хранения значений в базе использовалась встроенная база H2. Этот вид реализации также сохраняет в папке PAGES .html страницу, а далее сохраняет информацию о количестве в базе данных в следующем виде: 

**ID &emsp;&emsp;&emsp;&emsp;  WORD &emsp;&emsp;&emsp;&emsp; LINK &emsp;&emsp;&emsp;&emsp;  COUNT**

Консоль базы данных расположена на локальном хосте. ССылка: <http://localhost:8080/h2-console>\
Данные для подключения:
* Driver-class - org.h2.Driver
* JDBC URL - jdbc:h2:mem:testdb 
* username - sa
* password - password

База данных будет развернута до того момента, пока пользователь не введет q в консоль (в этот же момент приложение прекратит работу)
