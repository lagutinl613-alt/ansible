# AWX Roles Skeleton (no inventories, no playbooks)
Generated on 2025-09-13T07:21:35.918043Z

Содержимое:
- ansible.cfg — пути для ролей/коллекций
- collections/requirements.yml — коллекции Ansible
- roles/ (baseline_onboarding, firewall_ipset, node_health) — с defaults и tasks

Все переменные задавайте в AWX (Inventory/Host vars, Survey, Credentials). Секреты (SSH ключи, токены) держите только в Credentials.
