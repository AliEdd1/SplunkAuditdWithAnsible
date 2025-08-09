Ansible: Syslog-ng, Auditd, and Splunk UF
Automates installation and configuration of:

syslog-ng for local/system log routing
auditd to watch /etc (and more) for changes
Splunk Universal Forwarder to ship logs and audit events


📜 Purpose
This playbook sets up a complete logging pipeline with syslog-ng, auditd, and Splunk UF so you can:

Monitor critical system directories like /etc for changes.
Forward logs to a Splunk indexer for centralized analysis.
Automate setup across multiple servers.


📦 Requirements

Ansible 2.14+ (or newer)
Managed nodes: Linux (RHEL/CentOS/Alma/Rocky, Ubuntu/Debian)
SSH access with privilege escalation (become)
Splunk indexer reachable from target hosts


📁 Project Structure
inventory/
  hosts.yml
playbook.yml
roles/
  auditd/
    tasks/main.yml
  splunk_uf/
    tasks/main.yml
    templates/
      inputs.conf.j2
      outputs.conf.j2
      props.conf.j2
      transforms.conf.j2
  splunk_uf_install/
    tasks/main.yml
  syslog_ng/
    tasks/main.yml
    templates/
      syslog-ng.conf.j2


📖 Usage
Follow the steps below to run this Ansible playbook. Note: Hover over any code block to see a "Copy" button for easy copying.

✅ Step-by-Step Guide

Clone this repository
git clone https://github.com/AliEdd1/SplunkAuditdWithAnsible.git
cd SplunkAuditdWithAnsible


Update the inventory
Edit the inventory/hosts.yml file and add your target servers:
all:
  hosts:
    server1:
      ansible_host: 192.168.1.10
    server2:
      ansible_host: 192.168.1.11


Run the playbook

Dry run (check mode)
ansible-playbook -i inventory/hosts.yml playbook.yml --check


Apply changes
ansible-playbook -i inventory/hosts.yml playbook.yml


Run only syslog-ng
ansible-playbook -i inventory/hosts.yml playbook.yml --tags syslog


Run only auditd
ansible-playbook -i inventory/hosts.yml playbook.yml --tags auditd






💡 Tip: Use --limit to run against a specific host:
ansible-playbook -i inventory/hosts.yml playbook.yml --limit server1


🔐 Secrets
Use Ansible Vault to store sensitive data like Splunk tokens:
ansible-vault create group_vars/vault.yml

Reference them in your variables as:
splunk_uf_hec_token: "{{ vault_splunk_hec_token }}"

