# `Ansible Mosquitto Playbook`

This is an Ansible role to configure a simple MQTT Server and is able to configure some bridges - e.g. for devices which are not supporting TLS. The bridge things forked from [uhlig-it](https://github.com/uhlig-it/ansible-role-mosquitto-bridge) thanks!

This playbook also includes TLS Settings and ships some fail2ban rules!


# Variables

The role uses the following variables to configure Mosquitto bridges:

```yaml

mosquitto_users:
- name: device
  password: whatever-ever-ever

mosquitto_tls:
  port: 8883
  certfile: /etc/mosquitto/certs/domain.cer
  keyfile: /etc/mosquitto/certs/domain.key
  cafile: /etc/mosquitto/certs/ca.cer
  require_certificate: False
  tls_version: tlsv1.2

mqtt_bridges:
- name: idIOT
  address: mqtt.example.com
  port: 8883
  user: idiot
  password: supersigrid
  topics:
  - "# both 0"
  ca_path: /etc/ssl/certs
```