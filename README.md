# SystemD

Стенд поднят на Vagrant с боксом Ubuntu/Jammy64

1. Написать service, который будет раз в 30 секунд мониторить лог на предмет наличия ключевого слова (файл лога и ключевое слово должны задаваться в /etc/default).

Создаём файл с конфигурацией для сервиса `/etc/default/watchlog`

Создаём лог с ключевым словом `/var/log/watchlog.log`

Создаём скрипт `/opt/watchlog.sh` и даём права на исполнение `chmod +x /opt/watchlog.sh`

Создаём юнит для сервиса `/etc/systemd/system/watchlog.service`

Создаём юнит для таймера `/etc/systemd/system/watchlog.timer`

Стартуем таймер `systemctl start watchlog.timer`

Проверяем `tail -n 1000 /var/log/syslog  | grep Master`

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/watchlog.jpg)

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/watchlog1.jpg)

2. Установить spawn-fcgi и создать unit-файл (spawn-fcgi.sevice)

Предварительно устанавливаем spawn-fcgi `apt install spawn-fcgi php php-cgi php-cli \
 apache2 libapache2-mod-fcgid -y`

Создаём конфиг в `/etc/spawn-fcgi/fcgi.conf`

Создаём юнит в `/etc/systemd/system/spawn-fcgi.service`

Стартуем `systemctl start spawn-fcgi`

Проверяем `systemctl status spawn-fcgi`

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/spawn-fcgi.jpg)

3. Доработать unit-файл Nginx (nginx.service) для запуска нескольких инстансов сервера с разными конфигурационными файлами одновременно.

Cоздаём новый Unit для работы с шаблонами (/etc/systemd/system/nginx@.service) (файл прилагается)

Дорабатываем конфиги Nginx-first и Nginx-second (/etc/nginx/nginx-first.conf, /etc/nginx/nginx-second.conf) (файлы прилагаются)

Стартуем сервисы 

`systemctl start nginx@first`

`systemctl start nginx@second`

Проверяем `ss -tnulp | grep nginx`

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/nginx.jpg)
