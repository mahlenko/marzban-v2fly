# Marzban Update Geosite

Этот репозиторий предназначен для автоматического скачивания базы V2Fly и передачи (прокидывания) этих баз в docker контейнеры **Marzban** и **Marzban-Node**.  

Скрипты обеспечивают актуализацию данных geosite для корректной работы прокси-сервера и связанных компонентов.

## Для marzban

Скачайте файл скрипта на сервер

```sh
wget -O v2fly_marzban.sh https://raw.githubusercontent.com/mahlenko/marzban-update-geosite/refs/heads/main/v2fly_marzban.sh && chmod +x v2fly_marzban.sh
```

Отредактируйте docker-compose `/opt/marzban/docker-compose.yml` добавьте в volumes каталог с новой БД:

```yml
services:
  marzban:
    ...
    volumes:
      ...
      - /var/lib/marzban/xray:/usr/local/share/xray
```

Скачайте БД и перезапустите панель
```sh
./v2fly_marzban.sh && marzban restart
```

## Для marzban-node

Скачайте файл скрипта на сервер

```sh
wget -O v2fly_node.sh https://raw.githubusercontent.com/mahlenko/marzban-update-geosite/refs/heads/main/v2fly_node.sh && chmod +x v2fly_node.sh
```

Отредактируйте docker-compose `/opt/marzban-node/docker-compose.yml` добавьте в volumes каталог с новой БД:

```yml
services:
  marzban:
    ...
    volumes:
      ...
      - /var/lib/marzban-node/xray:/usr/local/share/xray
```

Скачайте БД и перезапустите ноду
```sh
./v2fly_node.sh && marzban-node restart
```

## Автоматическое обновление

Добавьте задачу в crontab: 
```0 0 * * * {path_to_script}/v2fly_marzban.sh``` 

для marzban-node
```0 0 * * * {path_to_script}/v2fly_node.sh```
