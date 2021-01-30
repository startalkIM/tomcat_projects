### Instruction  
This is a repo for unzipped and after compiling Startalk Java services including  
+ [qfproxy](https://github.com/startalkIM/qfproxy)  
+ [push_service](https://github.com/startalkIM/push_service)
+ [im_http_service](https://github.com/startalkIM/im_http_service)

~~and a unpackaged tomcat v8.5.37 .  ~~  

These three services are obligatory for running Startalk properly. Each service exists at a independent tomcat and occupies different
ports. Check their project repo mentioned above for more details.  

### Deployment  

+ If you are deploying with our offcial guide at https://github.com/startalkIM/Startalk/blob/master/source-build.md, follow the steps:
```
mkdir -p /startalk/tomcat &&
cp -r ./  /startalk/tomcat/ &&
/startalk/tomcat/im_http_service/bin/catalina.sh &&
/startalk/tomcat/qfproxy/bin/catalina.sh &&
/startalk/tomcat/push_service/bin/catalina.sh 
sudo netstat -antpu|grep -E '8081|8082|8083'
```
From the netstat command result you can ensure the services are running properly.

+ If you would like to integrated these in your own tomcats enviroment, pay attention to change the setting related to tomcat:
```
1.change ports used by editting each projects conf/server.xml 
2.remove the setting of catalina in each projects bin/catalina.sh:
CATALINA_HOME=/startalk/tomcat/im_http_service
CATALINA_BASE=/startalk/tomcat/im_http_service
```
