# jMeterCasinoTest

Запускаем нагрузочные тесты (предаврительно должен быть установлен maven последней версии http://maven.apache.org/download.cgi, добавлена перменная окружения M2_HOME и путь до mvn.cmd добавлен в PATH):

- mvn clean verify 

Внимание: первый запуск будет достаточно долгим, т.к. maven требуется выгрузить все требуемые для JMeter библиотеки и загрузить их в локальное хранилище пользователя, кроме того требуется выгрузить ещё некоторые плагины которые были использованы в процессе написания тестов (например для функции base64Encode).  

Значения по умолчанию:

- numberOfThreads (количество нитей/потоков): 10
- serverName (адрес тестируемого сервера): test-api.d6.dev.devcaz.com
- serverPort (порт тестирумого сервера): 80
- username (имя пользователя для авторизации в basic auth): front_2d6b0a8391742f5d789d7d915755e09e
- password (пароль пользователя для авторизации в basic auth): (пустой)
- CSVFileWithISO4217 (CSV файл с кодами денежных единиц по стандарту ISO4217): codes-all_csv_for_test.csv (файл содержит только единицу RUB, т.к. на тестируемом экземпляре приложения доступна только она, см. http://joxi.ru/VrweoEqu7dyqw2. Кроме того в проекте ещё лежит 2 файла с денежными единицами: codes-all_csv_for_test2.csv - 5 различных единиц, включая RUB и codes-all_csv_for_test.csv - полный набор денежных единиц по состоянию на 22.11.2019)

Если нужно изменить значения по умолчанию (параметризовать значения выше) то нужно выполнить команду mvn clean verify с соответствущими изменяемыми параметрами (название параметра должно начинаться с D), например:

- mvn clean verify -DnumberOfThreads=5 -DserverName=test-api.d6.dev.devcaz.com -DserverPort=80 -Dusernamebasic=front_2d6b0a8391742f5d789d7d915755e09e -Duserpasswordbasic= -DCSVISO4217File=codes-all_csv_for_test2.csv

Отчет в формате CSV расположен в jMeterCasinoTest\target\jmeter\results\test.csv. Кроме того доступен более полный визуальный отчет в jMeterCasinoTest\target\jmeter\reports\test\index.html.
