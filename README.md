
# 1- Lighthouse Role

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

  
# 2 - Vector Role

Роль устанавливает и настраивает систему логирования **Vector**.

## Description

- Устанавливает Vector
- Создаёт конфигурационный файл `/etc/vector/vector.toml`
- Запускает и включает службу Vector

## Role Variables

Переменные по умолчанию находятся в `defaults/main.yml`:

vector_version: "0.41.1"
vector_config_path: "/etc/vector/vector.toml"
vector_sources:
  - type: "stdin"
vector_sinks:
  - type: "console"
    encoding: "json"

## Example

- name: Install Vector
  hosts: vector
  roles:
    - role: vector-role


## Requirements

- Ansible 2.10+

- Linux distribution with systemd
