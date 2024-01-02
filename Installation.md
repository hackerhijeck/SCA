## Sonatype Nexus3 Installation

### Steps of Installation:
```
$ apt update

## Java jdk 8 install first:
$ wget https://builds.openlogic.com/downloadJDK/openlogic-openjdk/8u392-b08/openlogic-openjdk-8u392-b08-linux-x64-deb.deb
$ dpkg -i <deb-file>.deb 
$ mkdir /app && cd /app

## Nexus tar file download:
$ wget https://download.sonatype.com/nexus/3/nexus-3.39.0-01-unix.tar.gz
$ tar -xvf nexus-3.39.0-01-unix.tar.gz
$ mv nexus-3.39.0-01 nexus
$ adduser nexus   (next steps of username and password)
$ chown -R nexus:nexus /app/nexus
$ chown -R nexus:nexus /app/sonatype-work

## Uncomment run_as_user parameter and set it as following:
=> run_as_user="nexus"
$nano  /app/nexus/bin/nexus.rc

## For start:
$./app/nexus/bin/nexus start
$./app/nexus/bin/nexus status

## Browser access:
http:localhost:8081

## If not working:
$ firewall-cmd --add-port=8081/tcp --permanent
$ firewall-cmd --reload

## For password:
$ cat /app/sonatype-work/nexus3/admin.password

## Setup a new password
```
