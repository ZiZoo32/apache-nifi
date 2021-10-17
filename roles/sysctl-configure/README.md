
# Настройка sysctl и limits 

## Данный репозиторий является ролью Ansible

- Устанавливает необходимые параметры в /etc/sysctl.d/00-tuneup.conf
- Устанавливает необходимые параметре для limits_params
- Значения name и value для sysctl указаны в defaults
- Параметры задаются в виде:
  - имя:
  - value: "значение"

### Пример ansible-playbook

    - hosts: sysctl-configure
      roles:
        - sysctl-configure
      become: true
      gather_facts: true
      vars:
        sysctl_params:
          fs.file-max:
            value: "2097152"
          fs.inotify.max_user_instances:
            value: "1024"
          fs.protected_hardlinks:
            value: "1"
        limits_params:
          param1:
            domain: "*"
            type: "hard"
            item: "nproc"
            value: "65535"
