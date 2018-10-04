### Ansible role for [influxdb](https://www.influxdata.com/time-series-platform/influxdb/) (open source edition)

##### Description
Installs influxdb from packages (from InfluxData repository), configures and starts it.  
This role is rather big and supports most of parameters in InfluxDB config.  
At the moment of writing, this ansible role has been synced with [influxdb 1.6.3 config](https://github.com/influxdata/influxdb/blob/389de31c961831de0a9f4172173337d4a6193909/etc/config.sample.toml)
All settings have their default values

##### Configuration
For a list of available variables, you need to take a look at [default vars file](https://github.com/rlex/ansible-role-influxdb/blob/master/defaults/main.yml)

##### To be done
1) User management
2) Database management

