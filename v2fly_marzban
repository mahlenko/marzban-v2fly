#!/bin/bash

XRAY_GEODATA_DIR="/var/lib/marzban/xray"

if [ ! -d "$DIR" ]; then
    mkdir -p "$XRAY_GEODATA_DIR"
fi

cd "$XRAY_GEODATA_DIR"

# скачивание файлов
wget -O geosite.dat https://github.com/v2fly/domain-list-community/releases/latest/download/dlc.dat
wget -O geoip.dat https://github.com/v2fly/geoip/releases/latest/download/geoip.dat
