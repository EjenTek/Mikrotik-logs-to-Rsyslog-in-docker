# Mikrotik-logs-to-Rsyslog-in-docker

## Описание проекта 

### Этот проект предоставляет простое решение для централизованного сбора логов с устройств MikroTik с использованием rsyslog в контейнере Docker.
Он включает:
- Ротацию логов (один файл на день).
- Ограничение размера файлов.
### Возможности 
- Централизованный сбор логов: Собирайте логи с устройств MikroTik в одном месте.
- Ротация логов: Ежедневные файлы логов с периодом хранения (например, 30 дней).
- Ограничение размера файлов: Ограничьте размер файлов, чтобы предотвратить переполнение диска.
- Основано на Docker: Простое развертывание с помощью Docker Compose.
### Требования 
-Docker и Docker Compose установлены на вашем сервере.
-Устройство MikroTik, настроенное для отправки логов на syslog-сервер.

## Установка

### 1. Клонируйте репозиторий
```
git clone https://github.com/yourusername/rsyslog-mikrotik.git
cd rsyslog-mikrotik
```

### 2. Запустите контейнер rsyslog
```
docker compose up -d
```

### 3. Настройте MikroTik
Перейдите в System -> Logging.
В закладке "Rules" выберите тип события который вы хотите отправлять в Rsyslog (например Firewall) и установите для него "Action" = remote.

<img width="301" height="224" alt="image" src="https://github.com/user-attachments/assets/fcfb713e-6161-4769-b219-3114130a8b2b" />

Перейдите к вкладке "Action". Выберите строку "remote". Укажите адрес вашего Rsyslog в строке "Remote Address".

<img width="405" height="353" alt="image" src="https://github.com/user-attachments/assets/9a429086-c920-4458-8281-6ff75deb0fd6" />

### 4. Проверьте логи на Rsyslog
```
ls -la logs/
tail -f logs/$(date +%Y-%m-%d).log
```

## Конфигурация.
- Логи хранятся в папке logs/.
- Настройки работы Rsyslog находятся в config/rsyslog.conf

## Лицензия / License
MIT License. See LICENSE for details.
