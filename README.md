# Отчёт

## docker history

### Запуск контейнера redis и проверка что он запущен

<img width="856" height="665" alt="1" src="https://github.com/user-attachments/assets/3b063a25-799f-4395-b88b-4424910ae3ce" />

### Далее создаётся приложение rocketcounter из образа `rotorocloud/rocket-counter` и его публикация на порту 8085
<img width="1041" height="161" alt="2" src="https://github.com/user-attachments/assets/f3cd4250-4321-4b9b-a300-95387cf1720b" />

Через `docker ps` смотрим что контейнер запущен и связан с указанными портами

---

Проверка что приложение работает

<img width="400" height="400" alt="3" src="https://github.com/user-attachments/assets/7c06af81-2201-459f-a92d-a7a7b3ab385b" />
<img width="400" height="400" alt="4" src="https://github.com/user-attachments/assets/2407525d-82cd-4dc5-a618-892635c14f91" />

Командой `curl.exe -s localhost:8085` выводим HTML код
<img width="891" height="536" alt="5" src="https://github.com/user-attachments/assets/3672ad54-4839-4156-adeb-c96d01fe4867" />

Команда `curl -s localhost:8085 | head` выводила ошибку, поэтому пришлось её заменить на эквивалентную

<img width="1467" height="176" alt="ошибка" src="https://github.com/user-attachments/assets/68d91382-9e53-454e-b30e-27c6eed16220" />

---

### Запуск через `docker-compose.yml`

После создания директории и самого `.yml` файла он был запущен в Docker

Стоит отметить что тут использовался тот `docker-compose.yml` что сейчас лежит в репозитории, за исключением описания портов. На этой итерации вместо
```yaml
ports:
  - "0:5000"
```
Было написанно

```yaml
ports:
  - "8085:5000"
```

<img width="1136" height="167" alt="6" src="https://github.com/user-attachments/assets/07a08cca-5e5c-47f4-9d14-85bcced8928e" />

Для проверки работы проделал те же шаги что и ранее

<img width="700" height="500" alt="7" src="https://github.com/user-attachments/assets/e2601937-a0d6-439e-a0a4-83ac2b60a4d7" />
<img width="500" height="500" alt="8" src="https://github.com/user-attachments/assets/7d9c761e-a3c3-4b35-8f36-f074e404fcac" />

---

### Масштабирование приложения

Уже теперь пишем в `docker-compose.yml` и запускаем 2-мя экземплярами

```yaml
ports:
  - "0:5000"
```
<img width="1453" height="243" alt="11" src="https://github.com/user-attachments/assets/d6db851e-fada-4a6f-8b39-199461b42852" />

Теперь можно получить доступ к приложению через 2 порта (счётчик для них общий)


<img width="919" height="993" alt="13" src="https://github.com/user-attachments/assets/ac737c8c-fec6-45f9-a592-9f6b4b854fa9" />
<img width="936" height="1004" alt="14" src="https://github.com/user-attachments/assets/67025d6f-5dcb-4175-937b-f56197021251" />

Проверил не только на вкладках, но и через команду

<img width="806" height="468" alt="12" src="https://github.com/user-attachments/assets/697d8ca2-3bf3-4eae-81f5-49d3d90d7577" />


