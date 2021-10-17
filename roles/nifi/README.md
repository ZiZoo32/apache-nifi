
# Установка и конфигурирование Apache NIFI

## Данный репозиторий является ролью Ansible

- Устанавливает standalone Apache NiFi
- Создаёт пользователя и группу nifi
- Создаёт самоподписанные сертификаты 
- Наcтраивает параметры конфигурации через Apache NiFi ToolKit


### Зависимости (dependencies)

Данная роль имеет зависимости (указаны в meta/main.yml)

- роль **sysctl-configure** - настройка параметров sysctl и limits


### Конфигурирование WildFly

    java: - версия пакета java (по умолчанию - "java-1.8.0-openjdk")

    nifi_user - системный пользователь NiFi 
    nifi_group - группа пользователя NiFi
    nifi_password - пароль

    nifi_version - версия пакета NiFi
    nifi_root - путь в системе, куда будет установлен NiFi (по умолчанию - "/opt")

    nifi_admin - Администратор NiFi
    nifi_ou - Домен (Organizational Unit) NiFi


### Пример ansible-playbook

    - hosts: nifi
      roles:
        - nifi
      gather_facts: true
      vars:
        nifi_user: "nifi"
        nifi_group: "nifi"  
        nifi_password: "qwerty123"

        nifi_admin: "admin"
        nifi_ou: "Apache_NIFI"

