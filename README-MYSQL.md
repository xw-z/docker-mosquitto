
```
vi /etc/mosquitto.d/auth-plugin.conf
```

```
auth_plugin /usr/lib/auth-plug.so
auth_opt_backends mysql
auth_opt_host 127.0.0.1
auth_opt_port 3306
auth_opt_dbname dbname
auth_opt_user root
auth_opt_pass root
auth_opt_userquery SELECT pw FROM t_mqtt_users WHERE username = '%s' limit 1
auth_opt_superquery SELECT COUNT(1) FROM t_mqtt_users WHERE username = '%s' AND super = 1
auth_opt_aclquery SELECT topic FROM t_mqtt_acls WHERE (username = '%s') AND (rw & %d)>0
```