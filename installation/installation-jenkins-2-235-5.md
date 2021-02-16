## Jenkins 2.235.5 Installation Manual

##### Component

- machine with OS RedHat 7
- java-1.8.0-openjdk-1.8.0.242.b08-1.el7.x86_64.rpm
- jenkins.war


### 1.) Create User for Jenkins
- Run as root

Exec command:
```
groupadd jnkadm -g 5200
useradd jnkadm -u 5201 -s /bin/bash -d /home/jnkadm -g jnkadm
echo jnkadm | passwd --stdin jnkadm
```

### 2.) Install Jenkins
- Run as root
- assume jenkins package are on /Source
Exec command:
```
cd /Source/
yum install java-1.8.0-openjdk.x86_64 -y
```
Add Environment Variables for Java
In order to help Jenkins locate the JVM properly, you need to set two environment variables: "JAVA_HOME" and "JRE_HOME":
```
export JAVA_HOME=/usr/lib/jvm/jre-1.8.0-openjdk
export JRE_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.181-7.b13.el7.x86_64/jre
```

### 3.) Start Jenkins
- Run as jnkadm
Exec command:
```
USER: jnkadm
java -jar jenkins.war &   
```

### 4.) Open Firewall for Jenkins
- Run as root
Exec command:
```
firewall-cmd --zone=public --add-port=8080/tcp --permanent
firewall-cmd --reload
firewall-cmd --list-all
```
