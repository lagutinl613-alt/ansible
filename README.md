# AWX Project (Onboarding, Firewall+ipset, Node Health)
Generated on 2025-09-13T06:41:58.418552Z

## Playbooks
- `playbooks/01_baseline_onboarding.yml` — пункт 1
- `playbooks/06_firewall_ipset_setup.yml` — пункт 6 (установка)
- `playbooks/06_firewall_ipset_ban.yml` — пункт 6 (бан)
- `playbooks/06_firewall_ipset_unban.yml` — пункт 6 (разбан)
- `playbooks/17_node_health.yml` — пункт 17

## Как использовать
1. Замените `baseline_admin_ssh_pubkey` в `inventories/group_vars/all.yml` на ваш публичный ключ.
2. В AWX создайте Project, укажите этот архив (или разместите содержимое в вашем Git).
3. Создайте Inventory и импортируйте `inventories/hosts.yml`.
4. Создайте Job Templates:
   - Baseline Onboarding → `playbooks/01_baseline_onboarding.yml` (hosts: agents)
   - Firewall Setup → `playbooks/06_firewall_ipset_setup.yml`
   - Emergency Ban → `playbooks/06_firewall_ipset_ban.yml` (Survey: ip, ttl)
   - Unban → `playbooks/06_firewall_ipset_unban.yml` (Survey: ip)
   - Node Health → `playbooks/17_node_health.yml` (Schedule: по вкусу)
5. (Опционально) Укажите `health_alert_webhook` в group_vars, чтобы слать уведомления.

## Примечания
- Скрипт `firewall-restore.service` сохранит и восстановит ipset/iptables правила после перезагрузки.
- Для nftables напишите, я добавлю вариант с `nft set`.
