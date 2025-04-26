# Начало работы с PHP

## Настройка рабочего окружения
- PHP-интерпретатор
- Apache Server
- MySQL

### Настраиваем РО через Docker-образ
1. Установить Docker
2. Скачать ZIP-архив с https://github.com/sprintcube/docker-compose-lamp
3. Создать папку на локальном хосте (например, "PHP")
4. Разархивировать скачанный файл в созданную папку (удалить постфикс '-master')
5. Открыть IDE Terminal (VS Code), ввести команды:
   - cp sample.env .env (копирование содержимого из sample в .env)
   - docker compose up -d (собираем образ)
6. Переходим в Docker, видим образ 'lamp'
