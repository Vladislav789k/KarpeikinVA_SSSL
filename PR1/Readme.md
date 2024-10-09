
## Создаем 2 виртуальные машины на базе Ubuntu (Ссылка - https://ubuntu.com/download/desktop) и обеспечиваем между ними сетевой обмен.
![image](1.png)


![image](2.png)

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/318368be-6efa-42b8-a800-bedc86a8fe9e)


## Устанавливаем, включаем правила TCP и UDP соединения и настраиваем правила rsyslog на сервере и клиенте

**Установка и насйтрока на сервере**

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/244fc883-faa1-482f-9094-dc5ce1225aa8)

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/628f2bc4-84bd-4cb1-a844-3037fd26d9f2)






**Установка и настройка на клиенте**
![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/7ede59d6-8b0b-469a-9725-a4cc0dcf61f7)



![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/370f786e-2a0a-451d-ad62-38b5be2932a1)


![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/9fc7c0c0-156b-4a5c-94f5-1603c46ab904)




## Проверяем получения логов на сервере

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/e8384202-35a6-4857-a439-f94f4caea141)



## Устанавливаем и настраиваем получение логов на сервере с использованием Loki (Предварительно установив docker-compose)
![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/b00a9972-2880-4d72-b068-7c7a5d9ae595)

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/9a012b09-c1b1-48de-aa3d-7d3127a96ec0)


## Редактируем promtail и docker-compose на клиенте

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/d18c2063-aee7-42d8-95c8-967064b519e8)


![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/dfa87ebf-e7cd-45a0-ab45-603fb3b07024)



## Просматриваем логи клиента в Grafana

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/ea87dfee-b722-431d-a8f3-f9c59c4bee52)

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/b7d49aa1-5579-40a2-a180-c7dd49a97403)




## Установка получения логов на сервере с использованием Signoz
**Установка Signoz выполнена согласно инструкции с сайта: https://signoz.io/docs/install/docker/#install-signoz-using-docker-compose**

![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/5360ec82-5552-4ed0-8846-85dd280dcab1)


## Установка и настройка sample-nodejs-app на клиенте 
**Установка sample-nodejs-app выполнена согласно инструкции с сайта https://github.com/SigNoz/sample-nodejs-app**


![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/d62c474d-f79f-49c2-8886-77b5d7678c5e)



## Проверка получения логов в Signoz
![image](https://github.com/Vladislav789k/TOIB-PR4/assets/71137501/b32d90d4-1411-4c26-8c2e-f24e81c3fa62)

