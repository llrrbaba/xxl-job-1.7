### 配置部署调度中心

###### 1.修改相关配置文件

```pro
/xxl-job-1.7/xxl-job-admin/src/main/resources/xxl-job-admin.properties

# 数据源 相关配置
xxl.job.db.driverClass=com.mysql.jdbc.Driver
xxl.job.db.url=jdbc:mysql://192.168.17.133:3306/test
xxl.job.db.user=root
xxl.job.db.password=root

### xxl-job email
xxl.job.mail.host=smtp.163.com
xxl.job.mail.port=25
xxl.job.mail.username=rocker_pg@163.com
xxl.job.mail.password=APPLE9527chc
xxl.job.mail.sendFrom=rocker_pg@163.com
xxl.job.mail.sendNick=《任务调度平台XXL-JOB》

# xxl-job login
xxl.job.login.username=admin
xxl.job.login.password=admin
```

这里我修改了下数据库的连接参数，邮箱的用户信息，调度中心的登录密码



```proper
/xxl-job-1.7/xxl-job-admin/src/main/resources/log4j.properties

log4j.rootLogger=info,console,logFile

log4j.appender.console=org.apache.log4j.ConsoleAppender
log4j.appender.console.layout=org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern=%d - xxl-job-admin - %p [%c] - <%m>%n

log4j.appender.logFile=org.apache.log4j.DailyRollingFileAppender
log4j.appender.logFile.File=/Users/leeco/studyprojects/logs/applogs/xxl-job/xxl-job-admin.log
log4j.appender.logFile.layout=org.apache.log4j.PatternLayout
log4j.appender.logFile.layout.ConversionPattern=%d - xxl-job-admin - %p [%c] - <%m>%n
```

这里修改了下log4j.appender.logFile.File的属性值，否则会报错，FileNotFindException



###### 2.执行编译&&登录

```she
cd xxl-job-admin && mvn clean package
```

将生成的xxl-job-admin-1.7.2.war扔到tomcat的webapps下，把项目跑起来，然后输入在上面的配置文件中设置的用户名密码登录即可