### Installing Jenkins on ubuntu 20.04
```
1. Create a ubuntu machine with 2 Core & 4 GB RAM
2. Login to machine an run sudo hostnamectl set-hostname jenkins && bash
ubuntu@jenkins:~$
3. Install JRE with sudo apt-get update -y && sudo apt-get install -y default-jre
4. Check Java version with java -version
```
### Sample Output
ubuntu@jenkins:~$ java -version
openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment (build 11.0.11+9-Ubuntu-0ubuntu2.20.04)
OpenJDK 64-Bit Server VM (build 11.0.11+9-Ubuntu-0ubuntu2.20.04, mixed mode, sharing)

### Setup ENV variables to be used by Jenkins
```
5. export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
6. sudo mkdir -p /JENKINS_HOME && sudo chown ubuntu:ubuntu /JENKINS_HOME
7. export JENKINS_HOME=/JENKINS_HOME
8. echo $JAVA_HOME && echo $JENKINS_HOME
```
### Sample output
```
ubuntu@jenkins:~$ echo $JAVA_HOME && echo $JENKINS_HOME
/usr/lib/jvm/java-11-openjdk-amd64
/JENKINS_HOME

9. Downnload Jenkins war cd ~ && wget https://get.jenkins.io/war/2.306/jenkins.war
10. Start Jenkins nohup java -jar jenkins.war &, press enter twice
```

### Sample Output post Jenkins start
```
ubuntu@jenkins:~$ nohup java -jar jenkins.war &
[1] 39330
ubuntu@jenkins:~$ nohup: ignoring input and appending output to 'nohup.out'
```

### Sample Output in JENKINS_HOME after Starting Jenkins
```
ubuntu@jenkins:~$ ls -ltr /JENKINS_HOME/
total 60
drwxrwxr-x 11 ubuntu ubuntu 4096 Aug 11 06:22 war
-rw-rw-r--  1 ubuntu ubuntu   64 Aug 11 06:22 secret.key
-rw-rw-r--  1 ubuntu ubuntu    0 Aug 11 06:22 secret.key.not-so-secret
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 11 06:22 plugins
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 11 06:22 jobs
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 11 06:22 nodes
-rw-rw-r--  1 ubuntu ubuntu  156 Aug 11 06:22 hudson.model.UpdateCenter.xml
-rw-------  1 ubuntu ubuntu 1712 Aug 11 06:22 identity.key.enc
-rw-rw-r--  1 ubuntu ubuntu  171 Aug 11 06:22 jenkins.telemetry.Correlator.xml
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 11 06:22 userContent
-rw-rw-r--  1 ubuntu ubuntu  907 Aug 11 06:22 nodeMonitors.xml
drwxrwxr-x  3 ubuntu ubuntu 4096 Aug 11 06:22 logs
drwxrwxr-x  3 ubuntu ubuntu 4096 Aug 11 06:22 users
drwx------  4 ubuntu ubuntu 4096 Aug 11 06:22 secrets
-rw-rw-r--  1 ubuntu ubuntu 1595 Aug 11 06:22 config.xml
drwxrwxr-x  2 ubuntu ubuntu 4096 Aug 11 06:22 updates
```

11. Access Jenkins Using http://3.15.199.147:8080 on browser the Jenkins Unlock
Get Initial Admin Password cat /JENKINS_HOME/secrets/initialAdminPassword
ubuntu@jenkins:~$ cat /JENKINS_HOME/secrets/initialAdminPassword
ec3e90ee616a4e4daa39a0a1bc7d3f79
Foloow the below Images to complete Raw Jenkins Setup Insert_Admin_Password Customize_Jenkins Select_None_plugin Create_First_User Instance_configuration Jenkins_ready 