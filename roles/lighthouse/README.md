
# Lighthouse Role

Роль устанавливает **Lighthouse** — веб-интерфейс для ClickHouse, работающий через nginx.

## Description

Роль выполняет следующие задачи:

- Устанавливает nginx
- Клонирует репозиторий Lighthouse
- Копирует файлы Lighthouse в `/var/www/lighthouse`
- Создаёт конфиг nginx для сервиса
- Запускает и включает nginx

## Role Variables

Переменные по умолчанию находятся в `defaults/main.yml`:


lighthouse_repo: "https://github.com/VKCOM/lighthouse.git"
lighthouse_dest: "/var/www/lighthouse"
nginx_lighthouse_conf: "/etc/nginx/sites-enabled/lighthouse.conf"
listen_port: 8080

## Example

- name: Install Lighthouse
  hosts: lighthouse
  become: true
  roles:
    - lighthouse-role


## Requirements

- Ansible 2.10+

- git установлен на целевой машине

- systemd-based OS

