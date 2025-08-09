# Ansible: Syslog-ng, Auditd, and Splunk UF

Automates installation and configuration of:
- syslog-ng for local/system log routing
- auditd to watch /etc (and more) for changes
- Splunk Universal Forwarder to ship logs and audit events

## Requirements
- Ansible 2.14+ (or newer)
- Managed nodes: Linux (RHEL/CentOS/Alma/Rocky, Ubuntu/Debian)
- SSH access with privilege escalation (become)

## Inventory example

`yaml
# inventory/hosts.yml
all:
  hosts:
    myserver1:
      ansible_host: 10.0.0.11
    myserver2:
      ansible_host: 10.0.0.12
