# Micropython TCP terminal
## TCP терминал для ESP8266/32 на micropython
Файлы для микроконтроллера лежат в папке ***/esp***, в **boot.py** необходимо ввести свои параметры подключения к WIFI.

При запуске/перезагрузке микроконтроллера, term.py самостоятельно пытается подключиться к компьютеру. Адрес удаленной ЭВМ указан в самом модуле, первоначально необходимо его правильно записать в переменную **host_addr**. Возможно правильнее будет поместить ***import agent.term*** в **boot.py**.

Также возможно подключение от компьютера к микроконтроллеру на порт 40, в term.py установлен callback на подключение. 
Подключаемся через netcat: **nc xx.xx.xx.xx 40**

## Постоянное подключение host.py
Первоначально были большие надежды на netcat, но версия для windows сильно урезана, и в итоге совсем не подошла. Решил написать своё решение - получился **host.py**. Скрипт постоянно прослушивает порт на подключение, взаимодествует с открытым соединением, при поступлении нового соединения, текущее разрывается. Это очень удобно, потому-что не пропускаем старт основной программы.
