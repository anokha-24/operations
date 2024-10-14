We are using a MySQL DB running on an Ubuntu Virtual Machine, external to the Kubernetes cluster.

Edit or add the following line to the file in the path `/etc/mysql/mysql.conf.d/mysqld.cnf`

```diff
- bind-address = 127.0.0.1 
+ bind-address = 0.0.0.0   
```
