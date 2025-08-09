# Ansible: Syslog-ng, Auditd, and Splunk UF

Automates installation and configuration of:
- syslog-ng for local/system log routing
- auditd to watch /etc (and more) for changes
- Splunk Universal Forwarder to ship logs and audit events

## Requirements
- Ansible 2.14+ (or newer)
- Managed nodes: Linux (RHEL/CentOS/Alma/Rocky, Ubuntu/Debian)
- SSH access with privilege escalation (become)

---

## Installation & Cloning

`bash
git clone https://github.com/AliEdd1/SplunkAuditdWithAnsible.git
cd SplunkAuditdWithAnsible
# Dry run
ansible-playbook -i inventory/hosts.yml playbook.yml --check

# Apply
ansible-playbook -i inventory/hosts.yml playbook.yml
