# SystemD

1. Написать service, который будет раз в 30 секунд мониторить лог на предмет наличия ключевого слова (файл лога и ключевое слово должны задаваться в /etc/default).

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/watchlog.jpg)

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/watchlog1.jpg)

2. Установить spawn-fcgi и создать unit-файл (spawn-fcgi.sevice)

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/spawn-fcgi.jpg)

3. Доработать unit-файл Nginx (nginx.service) для запуска нескольких инстансов сервера с разными конфигурационными файлами одновременно.

Cоздаём новый Unit для работы с шаблонами (/etc/systemd/system/nginx@.service) (файл прилагается)

Дорабатываем конфиги Nginx-first и Nginx-second (/etc/nginx/nginx-first.conf, /etc/nginx/nginx-second.conf) (файлы прилагаются)

Стартуем сервисы 

systemctl start nginx@first

systemctl start nginx@second

Проверяем ss -tnulp | grep nginx

![Image alt](https://github.com/NikPuskov/SystemD/blob/main/nginx.jpg)
