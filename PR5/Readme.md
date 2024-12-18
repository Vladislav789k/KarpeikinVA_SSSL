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
![image](https://github.com/user-attachments/assets/a2433792-b3f8-4921-b56f-b98b8f998681)
![image](https://github.com/user-attachments/assets/feb37eda-cfc2-4425-b790-eae65181c62e)
### Проверим версию suricata
![image](https://github.com/user-attachments/assets/611a8a96-c3ea-48b4-96c6-f1bf5dfd82b2)
![image](https://github.com/user-attachments/assets/cd338920-18d9-4a63-a7bc-52d566b1edbc)
![image](https://github.com/user-attachments/assets/a03ef630-09f0-4b65-88b2-da7dd6b251c2)


### Настройка suricata

![image](https://github.com/user-attachments/assets/391f715f-9752-4102-986f-b5865d703189)

### Suricata настроена и работает
### Добавим правила сканирования
![image](https://github.com/user-attachments/assets/c3401397-8138-4eee-a825-d67cb9cb5727)
![image](https://github.com/user-attachments/assets/89161788-d381-4ed1-acac-2b00577434e3)
![image](https://github.com/user-attachments/assets/ff2d023b-c833-4858-aafa-931eba5e8599)
### Проведём сканирование с кали машины
![image](https://github.com/user-attachments/assets/20224e39-670e-42d5-9d01-f77544dea576)
### Проверим логи suricata
![image](https://github.com/user-attachments/assets/83fc789b-ccc3-4d4f-8365-0988a82cb483)
### Видим сканирование.
### Установим nessus
![image](https://github.com/user-attachments/assets/aa72ca91-29fd-4eac-aa6c-1f810b9b190a)
![image](https://github.com/user-attachments/assets/43a6ca01-cd8f-4b8b-bb00-58491f47812b)
### Ошибка нессуса тк он запретил регион РФ в виду санкций.
![image](https://github.com/user-attachments/assets/a6f68032-2787-4b4d-9481-f8e018753b56)
### Установка openvas
![image](https://github.com/user-attachments/assets/0c5cd041-2442-444f-bce3-2aa3fdbf3fcc)
![image](https://github.com/user-attachments/assets/5d4fee49-71e2-4daa-80a2-ec5daed05cec)
### При установке OpenVas возникла проблема с бесконесной загрузкой, правда невозможно так долго ждать.
### Nessus не дает вообще скачаться (санкции выше).
### На работе использую сканер уязвимостей от Positive Technologies "MaxPatrol VM" или ScanOVAL по рекомендации ФСТЭК. Писал скрипты для ScanOVALа.
### Yara
![image](https://github.com/user-attachments/assets/b9863ff3-70ab-421f-bbbb-6f625bb36b89)
### Git clone 
![image](https://github.com/user-attachments/assets/3b73d9d9-ee34-46af-bf1e-44fb422559ee)
![image](https://github.com/user-attachments/assets/e32de0de-15d9-45c5-b68a-66d6226e8e02)
![image](https://github.com/user-attachments/assets/2164eef2-85a6-49ad-85ee-0c0f75b5c1e2)
![image](https://github.com/user-attachments/assets/d2dc83c3-abb1-4303-9ca4-a0d60a5966a4)




