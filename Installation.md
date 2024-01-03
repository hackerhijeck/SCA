## Sonatype Nexus3 Installation

### Steps of Installation Sonatype:
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

### Steps of Installation Sonatype IQ Server:
```
$ mkdir /opt/nexus-iq-server
$ cd /opt/nexus-iq-server
$ wget https://download.sonatype.com/clm/server/latest.zip
$ unzip latest.zip
$ chown -Rv {username} /opt/nexus-iq-server
$ nano config.yml
 database:
  type: postgresql
  hostname: localhost
  port: 5432
  name: iqserver
  username: admin
  password: admin
## For SQL Database:
$ apt install postgresql
$ systemctl start postgresql
$ sudo -u postgres psql
$ CREATE DATABASE iqserver;
$ CREATE USER admin WITH PASSWORD 'admin';
$ GRANT ALL PRIVILEGES ON DATABASE iqserver TO admin;
$ \q
$ nano /etc/postgresql/<version>/main/pg_hba.conf
  host    iqserver     admin     127.0.0.1/32    md5
$ systemctl restart postgresql

## Run
$ ./demo.sh

## Port:
http://localhost:8070

## Default credentials
admin
admin123

## For trial license:
https://my.sonatype.com/profile/licenses

## Install license key:
install the license key
```
