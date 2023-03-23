N@lled By: Nguyễn Trung Hậu<br>
Email: ken.hdpro@gmail.com<br>
Facebook: http://fb.com/haunguyenckc<br>

# INSTALL DIRECTADMIN ONLY CENTOS7 64BIT
```
# Install command for Directadmin 1604 only centOS7 x64
yum -y install wget && wget --no-cache -O setup.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/da-1604-centos7.sh" > tmp 2>&1
chmod +x setup.sh

# Install command for Directadmin 1620 only centOS7 x64
yum -y install wget && wget --no-cache -O setup.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/da-1620-centos7.sh" > tmp 2>&1
chmod +x setup.sh

# Install command for Directadmin 1620 only centOS8 x64
yum -y install wget && wget --no-cache -O setup.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/da-1620-centos8.sh" > tmp 2>&1
chmod +x setup.sh

# Install command for Directadmin 1624 only centOS7 x64
yum -y install wget && wget --no-cache -O setup.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/da-1624-centos7.sh" > tmp 2>&1
chmod +x setup.sh

# Install command for Directadmin 1624 only centOS8 x64
yum -y install wget && wget --no-cache -O setup.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/da-1624-centos8.sh" > tmp 2>&1
chmod +x setup.sh


# To Get Help
./setup.sh -h


# To Setup
./setup.sh m h p i n

option "m": Mode
+ auto: Auto setup version package (Default: Openlitespeed, PHP81, Mariadb)
+ normal: You can select version package with custombuild

option "h": Server hostname (Default: server.test.com)
+ xxx.yyy.zzz (Ex: server.hca.com)

option "p": Password admin
+ You can input password or input: "rand" -> for random password

option "i": IP server
+ Auto detect IP if input: detect | or you can input local ip server (Command: "ip a" to show local ip server)

option "n": Network Card (Default: hca)
+ For using license.key, Directadmin 1604 no needed config option "n", Other Directadmin version needed config "n"
+ Input network card  attached IP Server


Ex: Install DA 1604 in VPS (Do nothing)
./setup.sh auto server.nguyentrunghau.me admin@123
+ Mode: auto | Host: server.nguyentrunghau.me | Pass: admin@123 | IP auto detect | Card: hca

Ex: Install DA version > 1604 in VPS (Set network card for run)
./setup.sh auto server.nguyentrunghau.me rand detect eth0
+ Mode: auto | Host: server.nguyentrunghau.me | Pass random | IP auto detect | Card: eth0

Ex: Install DA version > 1604 in Local Server (Set local IP and network card for run)
./setup.sh auto server.nguyentrunghau.me admin@123 1.2.3.4 eth0
+ Mode: auto | Host: server.nguyentrunghau.me | Pass: admin@123 | IP: 1.2.3.4 | Card: eth0

Ex: Install DA 1604 in Local Server (Set local IP for run)
./setup.sh auto server.nguyentrunghau.me rand 1.2.3.4
+ Mode: auto | Host: server.nguyentrunghau.me | Pass random | IP: 1.2.3.4 | Card: hca
	
... You can select option!
	
```

# CONFIG NETWORK IF YOU CONFIG FAIL
```
# Download File And View Your VPS Network Card
wget --no-cache -O network.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/network.sh
chmod +x network.sh
ip a | grep "inet .* brd .* scope global .* "

# Then Enter Exactly Name Of Your Network Card Attached To The Ip Server ($1 Is Your NetworkCard Name)
./network.sh $1


# Ex: 
wget --no-cache -O network.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/network.sh
chmod +x network.sh
ip a | grep "inet .* brd .* scope global .* "

=> inet 123.123.123.123/23 brd 123.123.123.255 scope global dynamic eth0

# Then
./network.sh eth0

```

# INSTALL SSL FOR ADMINPAGE
```
# Point The Subdomain Server.XXX.YYY to IP Server (A Record)
wget --no-cache -O adminssl.sh "https://raw.githubusercontent.com/irf1404/DA_FILES/master/adminssl.sh
./adminssl.sh

```

# INSTALL MULTI PHP VERSION
```
cd /usr/local/directadmin/custombuild
./build set php1_release 8.1
./build set php2_release 7.4
./build set php3_release 7.0
./build set php4_release 5.6
./build set php1_mode lsphp
./build set php2_mode lsphp
./build set php3_mode lsphp
./build set php4_mode lsphp
./build php n
./build rewrite_confs

```
