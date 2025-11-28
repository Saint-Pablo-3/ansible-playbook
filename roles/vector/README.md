# Vector Role

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
