# polaris-store-mysql-opt

## 如何使用

#### 构建

执行构建脚本 `Makefile` 即可

```bash
# ${store_mysql_opt_plugin_version}: store-mysqlopt 插件版本，默认为 main 的最新 commit
# ${polaris_server_tag}: 北极星服务端版本信息，默认为 main 分支
make build STORE_MYSQL_OPT_PLUGIN_VERSION=latest POLARIS_SERVER_VERSION=${polaris_server_tag}
```

#### 配置文件调整

修改 **conf/polaris-server.yaml** 文件，参考下列配置调整 store 的配置信息

```yaml
# Storage configuration
store:
  ## Database storage plugin mysqlOptStore
  name: mysqlOptStore
  option:
    master:
      dbType: mysql
      dbName: polaris_server
      dbUser: ##DB_USER##
      dbPwd: ##DB_PWD##
      dbAddr: ##DB_ADDR##
      maxOpenConns: 300
      maxIdleConns: 50
      connMaxLifetime: 300 # Unit second
      txIsolationLevel: 2 #LevelReadCommitted
```
