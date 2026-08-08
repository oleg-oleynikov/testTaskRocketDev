# Развёртывание стека через Ansible

&gt; Автоматизированная настройка сервера с помощью Ansible + Docker Compose.

---

## Требования

- **Управляющая машина** машина с установленным `ansible`
- **Целевой сервер** с Ubuntu/Debian и доступом по SSH
- SSH-ключ для подключения без пароля

---

## Установка Ansible

На машине, с которой будет запускаться деплой:

```bash
# Ubuntu / Debian
sudo apt update && sudo apt install -y ansible

# Проверка
ansible --version
```
---

## Настройка hosts

Создайте файл hosts.ini рядом с плейбуком:

```ini
[webservers]
server1 ansible_host=192.168.1.100 ansible_user=username
```
Замените 192.168.1.100 и username на реальные IP и пользователя сервера.

---


## Подготовка к запуску

Настройте ansible vault командой

```bash
ansible-vault create group_vars/production/vault.yml
```

---

## Запуск плейбука

```bash
ansible-playbook -i hosts.ini setup.yaml --ask-vault-pass
```