创建项目

```shell
docker-compose.yaml up -d
```

项目创建完毕后，先加入 mysql 驱动：

```shell
# 将驱动复制进去
docker cp mysql-connector-java-5.1.39-bin.jar confluence66hack_confluence_1:/opt/atlassian/confluence/confluence/WEB-INF/lib/
# 更改所有者
docker-compose exec confluence chown daemon:daemon /opt/atlassian/confluence/confluence/WEB-INF/lib/mysql-connector-java-5.1.39-bin.jar
# 重启Confluence
docker-compose restart confluence
```

先进入 Confluence 进行初始设置，然后替换`atlassian-extras-decoder-v2-3.2.jar`文件，重启 Confluence 服务即可：

```shell
# 复制破解文件
docker cp atlassian-extras-decoder-v2-3.2.jar confluence66hack_confluence_1:/opt/atlassian/confluence/confluence/WEB-INF/lib/
# 更改破解文件所有者
docker-compose exec confluence chown daemon:daemon /opt/atlassian/confluence/confluence/WEB-INF/lib/atlassian-extras-decoder-v2-3.2.jar
# 更改破解文件权限
docker-compose exec confluence chmod 644 /opt/atlassian/confluence/confluence/WEB-INF/lib/atlassian-extras-decoder-v2-3.2.jar
# 重启Confluence
docker-compose restart confluence
```

Github 项目地址：https://github.com/XuQK/confluence-hacker.git
