<h2>Настройка NUT для IPPON 650 UPS с USB в Debian 10</h2>

1. Установка nut:  

```
# apt-get install nut
```
2. Выбрать драйвер и прописать в ups.conf  
Список драйверов: https://networkupstools.org/stable-hcl.html

```
# nano /etc/nut/ups.conf
[ippon]
driver = blazer_usb
port = auto
desc = "IPPON 650 UPS, USB interface"
```
3. Для запуска клиента и сервера на одном хосте:

```
# nano /etc/nut/nut.conf

MODE=standalone
```
4. Перезапуск сервера: 
 
```
# service nut-server restart
# upsdrvctl start
```
5. Прослушивание сервером локального интерфейса: 
```
# nano /etc/nut/upsd.conf

LISTEN 127.0.0.1 3493
```
6. Добавление пользователя
```
# nano /etc/nut/upsd.users

[upsmon]
password = secret
actions = SET FSD
instcmds = ALL
upsmon master
```
7. Настройка клиента 
```
# nano /etc/nut/upsmon.conf

MONITOR ippon@localhost 1 upsmon secret master
#эти настройки есть в конфиге по умолчанию
MINSUPPLIES 1
SHUTDOWNCMD "/sbin/shutdown -h +0"
POLLFREQ 5
POLLFREQALERT 5
HOSTSYNC 15
DEADTIME 15
POWERDOWNFLAG /etc/killpower
RBWARNTIME 43200
NOCOMMWARNTIME 300
FINALDELAY 5
```
8. Перезапуск сервисов и получение статуса
```
# service nut-server restart
# service nut-client restart
# upsc ippon@localhost
```

9. Отключение звука. Просмотреть все команды, отключить биппер, убедиться в отключенном состоянии.
```
# upscmd -l ippon
# upscmd ippon beeper.toggle
# upsc ippon  ups.beeper.status

```