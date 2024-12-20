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
![image](https://github.com/user-attachments/assets/de8e785e-09c9-4158-8a36-e81d8860b47c)
![image](https://github.com/user-attachments/assets/dae014fd-62c8-4fcc-ac47-1c8a051325e9)
![image](https://github.com/user-attachments/assets/50d66f5b-9ba5-4182-b066-b349b5e6a893)
Подозрительный домен: `honestimnotevil.com`
Название домена вызывает подозрения из-за своей провокационной природы ("честно, я не злой"), что может быть попыткой злоумышленников замаскировать свои намерения.
Такие имена доменов часто используют в тестовых или вредоносных инфраструктурах.

Большое количество запросов (2074 запросов)
Это аномальное количество DNS-запросов к одному домену, что может свидетельствовать о:
Подключении к Command & Control серверу.
Вредоносной программе, регулярно обращающейся к этому домену.

Длинные поддомены

Например:
`...b7f9090b8e40bac43eb80a.honestimnotevil.com`
`...291b4324545e080e82a0ea.honestimnotevil.com`

Длинные, случайно сгенерированные поддомены часто используются в доменной генерации (DGA — Domain Generation Algorithm), которая характерна для вредоносных программ.
Каждый новый поддомен может быть связан с уникальной сессией или устройством, участвующим в ботнете.

Связь с единственным хостом: `172.21.8.157`
Все запросы направлены на один IP-адрес (172.21.8.157).
Это может быть внутренний сервер или прокси для перенаправления запросов, но такой концентрации трафика стоит уделить внимание.

Нет прямых соединений (Direct Connections = 0)
Указано, что прямые соединения отсутствуют, что говорит о том, что злоумышленники могут использовать DNS-туннелирование для передачи данных через DNS-запросы.
Что меня смущает:
DNS-туннелирование или C2-активность

Количество запросов и странные поддомены сильно указывают на DNS-туннелирование или связь с Command & Control сервером.
DGA (Domain Generation Algorithm)

Автоматически сгенерированные поддомены и подозрительный основной домен усиливают вероятность того, что это вредоносная инфраструктура.
Аномальная активность в сети

Если это единственный хост (172.21.8.157), отправляющий такие запросы, он может быть скомпрометированным устройством.

## Lab 3 
Импортируем логи и переключаемся на них.
![image](https://github.com/user-attachments/assets/a4d685f0-319b-46b9-b177-a448252b474d)
![image](https://github.com/user-attachments/assets/f244a535-5a13-425d-969a-28a8874b07f7)
Анализируем адреса и вносим легитимные в safelist
![image](https://github.com/user-attachments/assets/9208f9ef-3d48-443d-b856-7f49e1939a6b)

Остается всего два адреса, проверим каждый через VirusTotal

![image](https://github.com/user-attachments/assets/ecc3bf6e-08fd-410f-9c37-959add95f241)
![image](https://github.com/user-attachments/assets/a7005e78-8c6b-4edd-861b-47f75ae01648)
![image](https://github.com/user-attachments/assets/51bdd454-6054-4cc0-bad3-77998f11c097)

Связь с вредоносной активностью

Метка DGA и упоминание Cobalt Strike усиливают подозрения, что домен используется для управления вредоносной активностью. 

Количество детекций

Один сервис отметили домен как вредоносный, что повышает вероятность его использования в атаках. Неопределённость IP-адреса


Свежесть данных

Анализ проводился 5 дней назад, что достаточно актуально для оценки текущей активности домена.
