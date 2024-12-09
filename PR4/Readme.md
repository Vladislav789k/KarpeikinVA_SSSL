# Практическая работа №4 Network Threat Hunting

Выполнил студент ББМО-02-23 Карпейкин В.А.

## Скачиваем и разворачиваем стенд
![image](https://github.com/user-attachments/assets/7beeef05-d376-46e3-ab98-4abbea71421e)

![image](https://github.com/user-attachments/assets/6e0816ff-4529-4d96-af97-faa0c21a8565)

Логинимся

![image](https://github.com/user-attachments/assets/a18ca71d-db49-4399-acf3-5c31913532b4)

![image](https://github.com/user-attachments/assets/2826d416-ce4f-4c44-85aa-f8e8064af7d7)


Добавляем адрес с траффиком к skype.com в safelist, как сказано в руководстве
![image](https://github.com/user-attachments/assets/8cafde9f-bcd9-4048-b84a-9e8945eb531c)

Конечный safelist

![image](https://github.com/user-attachments/assets/681901da-dbbc-4666-a6a6-064ec3b78208)

## Lab 1

Импортируем логи и переключаемся на них в стенде

![image](https://github.com/user-attachments/assets/3c330afd-090d-4533-bc0c-87cbe4591a39)

Выбираем нужный Database

![image](https://github.com/user-attachments/assets/591ad699-9985-42cd-8042-7ed9325af9bc)

Переходим в модуль beacon web и анализируем 

![image](https://github.com/user-attachments/assets/c564f9cb-3b79-4c0b-827a-34c3b05dec16)

![image](https://github.com/user-attachments/assets/017e8c1a-8c65-4c56-a4dd-5bbdda764dfe)

Анализ всех адресов показал, что - 

Высокий уровень согласованности метрик (99.70%):

Такая высокая согласованность (cumulative metric conformity) может свидетельствовать о регулярных, четко упорядоченных запросах от источника к целевому IP-адресу. 
Это может быть признаком Beaconing-а, когда зараженное устройство связывается с управляющим сервером (C2).

Общее количество соединений (3011):

Для одного IP-адреса это значительное количество соединений. Если это типично для сети, возможно, это не аномалия. Но если такая активность не ожидается (например, для обычного пользователя или устройства IoT), это может указывать на нежелательное поведение.
Равномерное распределение активности на графике:

Использование HTTP без шифрования:

Отсутствие HTTPS может означать, что данные передаются в незашифрованном виде, что рискованно. Для связи с C2-серверами часто используются такие незащищенные протоколы.

Практически все адреса связаны с Windows, так что добавляем их в safelist

Конечный safelist

![image](https://github.com/user-attachments/assets/bb04ba97-8575-496c-8ce5-4df0fb6f19c2)

Перейдём в модуль длительных соединений

![image](https://github.com/user-attachments/assets/d84c7423-4067-4d56-9a6e-4b1c382acf3e)

Всего 2 адресса, проверим их через VirusTotal
1ый адресс
![image](https://github.com/user-attachments/assets/92f10252-9615-496a-8309-d40af85028e9)
![image](https://github.com/user-attachments/assets/0495ee43-35f5-4b2b-baf1-60ac7f66b519)
![image](https://github.com/user-attachments/assets/58e8e725-2e42-43eb-b379-bd4cc0db2950)

2ой адресс
![image](https://github.com/user-attachments/assets/7a05e55d-a583-4445-b131-cfcf0aa9289b)
![image](https://github.com/user-attachments/assets/1d9f1ec0-7fe1-4f9f-a695-712ba8491ff8)
![image](https://github.com/user-attachments/assets/7a626f64-b829-4aed-be6d-acf4e36a3328)

VirusTotal пометил один из адресов, как вредоносный.

Подозрительная природа доменов
Связанные с IP домены `piensorcad6302755c.aiihosted.com` и `demo1.aiihosted.com` выглядят подозрительно:
Длинные, автоматически сгенерированные имена часто используются злоумышленниками для маскировки.
Домены связаны с поддоменами `aiihosted.com`, что может указывать на временную инфраструктуру (например, для фишинга, C2 или ботнетов).

Связь с DigitalOcean
Этот IP принадлежит хостинг-провайдеру `DigitalOcean`, который, как и другие публичные облачные провайдеры, часто используется для легальных целей. Однако злоумышленники также арендуют облачные серверы для вредоносной активности, таких как:
Развёртывание C2-серверов.
Проведение атак (например, DDoS, фишинг).

Связь с файлом `"7May2021_export_bookmark.html"`:
Хотя файл не был помечен как вредоносный, сама его природа (экспорт закладок) может намекать на использование IP для передачи данных, что требует дополнительного анализа.

## Lab 2

Импортируем логи и переключаемся на них.





