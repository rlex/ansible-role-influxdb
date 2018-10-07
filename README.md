### Ansible role for [influxdb](https://www.influxdata.com/time-series-platform/influxdb/) (open source edition)

##### Description
Installs influxdb from packages (from InfluxData repository), configures and starts it.  
Also can manage supported resources (users, databases, retention policies)  
This role is rather big and supports most of parameters in InfluxDB config.  
At the moment of writing, this ansible role has been synced with [influxdb 1.6.3 config](https://github.com/influxdata/influxdb/blob/389de31c961831de0a9f4172173337d4a6193909/etc/config.sample.toml)  
All settings have their default values where possible

##### Configuration
For a list of available variables, you need to take a look at [default vars file](https://github.com/rlex/ansible-role-influxdb/blob/master/defaults/main.yml)

##### Resource management
You can create users, databases and retention policies in influxdb from ansible. First of all, if you have auth enabled, you need to specify
```
influxdb_login_username: your_influxdb_admin_login
influxdb_login_password: your_influxdb_admin_password
```

Then you can manage users with this dict:

```
influxdb_users:
  - user_name: user1
    user_password: pass1
    state: present
  - user_name: user2
    user_password: pass2
    state: absent
  - user_name: user3
    user_password: pass3
    admin: yes
```

Same with databases:

```
influxdb_databases:
  - database_name: database1
  - database_name: database2
    state: absent
```

Sadly, at the moment of writing (ansible 2.6.2) ansible influxdb module does not support permission manegement, so you will still need to login and grant permissions manually:


```
GRANT ALL ON "database1" TO "user1"
```

Retention policies management:

```
influxdb_retention_policies:
  - policy_name: telegraf_metrics_keep_for_4_weeks
    database_name: telegraf_metrics
    duration: 4w
    default: true
  - policy_name: tpr_metrics_keep_for_4_weeks
    database_name: tpr_metrics
    duration: 4w
    default: true
```
