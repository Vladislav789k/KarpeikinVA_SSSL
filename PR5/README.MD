# Практика 5
## Карпейкин Владислав Анатольевич
## ББМО-02-23

### Начало
#### 2 ВМ
Работа была выполнена на 2 виртуальных машинах на базе ОС Ubuntu, client и server
![image](https://github.com/user-attachments/assets/aaa5e955-913c-405a-b1e3-ac05edfc424e)


#### Сетевой обмен
На виртуальных машинах был настроен сетевой мост
![image](https://github.com/user-attachments/assets/13563aff-a95b-4eb9-b8e0-e8b5c698056e)
![image](https://github.com/user-attachments/assets/c25d5781-01bd-4691-9274-fc687fdcf45b)


Проверка "видимости" ВМ друг для друга
![image](https://github.com/user-attachments/assets/2d6a7731-cb58-4925-8368-c0cf9745450f)


### Разворачивание сервера Wazuh
В ходе подготовки и разворачивания сервера были предприняты следующие шаги:
- Установка mc для удобства при редактировании текстовых файлов
- Обновление списка пакетов и установка новых
- Выполнили установку на версии 4.9
Ip серверной ВМ и первичная команда для curl.
![image](https://github.com/user-attachments/assets/b3b8898d-cc21-417e-a658-6bd692e43b1f)

Полученные после завершения установки логин и пароль от кабинета
![image](https://github.com/user-attachments/assets/3e4af6e7-9541-4bbf-a049-3338d38bacc8)
![image](https://github.com/user-attachments/assets/a862e821-3ae3-49e4-b8e2-4010469405e1)



Старотовый экран Wazuh без подключенного "агента"
![image](https://github.com/user-attachments/assets/3940c38c-3639-47bc-a6b0-25ab44d6b4eb)
![image](https://github.com/user-attachments/assets/1c6acd2f-121d-4568-bee1-18afcfde4038)

Добавление "агента"
![image](https://github.com/user-attachments/assets/1e8995ae-f004-4d11-b4ef-f508f605c0fb)
![image](https://github.com/user-attachments/assets/7a12d621-af5e-4dcf-b65d-df5326bb9f5b)

Выполнение команд на клиенте
![image](https://github.com/user-attachments/assets/c456cfa2-caf5-4a14-a129-4eb5f5be0cf5)


Экран Wazuh после подключения "агента"
![image](https://github.com/user-attachments/assets/39e23535-29d0-4c05-a675-013e1b2b5ca9)


Возможности про проверке "агента"
![image](https://github.com/user-attachments/assets/2ca09f49-9eac-4dec-a390-07f88313202b)


### Проверка целостности файлов

Результат проверки целостности файлов
![image](https://github.com/user-attachments/assets/a660715b-9877-4082-baf1-c5b7d1287adc)


В ходе выполнения задания были предприняты следующие шаги:
- Установили с какой переодинчостью будет проверяться содержимое директории "*/test"
- Создавали, редактивровали и удаляли файлы

### Выявление уязвимостей в соотстветвии с документацияей

Внесенные в conf файл изменения
![image](https://github.com/user-attachments/assets/f32e6afd-cc39-4b32-b27e-7054d128dad8)


Выявление уязвимостей пакетов на клиенте ("агенте")
![image](https://github.com/user-attachments/assets/74a16144-500d-48fa-9e32-8394bc9c81bb)

Выявленные Wazuh аномалии
![image](https://github.com/user-attachments/assets/7d1468ec-038f-417f-9872-1762ca6c0238)

![image](https://github.com/user-attachments/assets/7a301bda-43a3-4e34-bc02-6864097c54c4)
![image](https://github.com/user-attachments/assets/39ddb553-7d52-4c92-b9e7-8e40d022b22f)

### Suricata agent

### Блок для анализа логов Suricata


### На защищаемом клиенте поднята Apache


### Сканер уязвимостей Nikto


###   Wazuh Vulnerability detection


### OpenVas
При установке OpenVas возникла проблема с бесконесной загрузкой, правда невозможно так долго ждать.

Nessus не дает скачать (санкции).

У меня есть чкткое представление работы сканера уязвимостей (на работе исрользую решение от Positive Technologies "MaxPatrol VM" или ScanOVAL по рекомендации ФСТЭК)



### Yara



Качаем правила


