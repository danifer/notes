Debian server setup checklist including SSH, RAID monitoring, Dell OpenManage, firewall, Apache, nginx, MySQL, and backup configuration.

---

Things to check when setting up a new server:

check startup settings
run on both power supplies for a while
install debian

install sudo
    -add primary user

install ssh
    aptitude install ssh
    change ssh port to 1246
    disallow root users
change apt sources
update bios
    http://www.ducea.com/2007/08/27/dell-bios-firmware-updates-on-debian/

Do server burn in with "stress" aptitude install stress

setup remote management software (I've stopped doing this one)
    install ipmitool (Dell)
        modprobe ipmi_si
        modprobe ipmi_devintf
        aptitude install ipmitool

Setup RAID monitoring software (I like megactl) available from these guys as a debian package:
deb http://hwraid.le-vert.net/debian stable main

Write raid status to a file so we can update it later with a cron job

If it's a Dell machine, add openmanage
- Add the Dell repository to /etc/apt/sources.list :
        #Dell openmanage
        deb http://linux.dell.com/repo/community/deb/latest /
- aptitude install srvadmin-all
- restart the dataeng service: /etc/init.d/dataeng
- Add the Dell command path to /root/.bashrc :
        PATH=$PATH:/opt/dell/srvadmin/sbin
- Run 'source /root/.bashrc' to activate the change

- Example usage:
        root@ying:~> omreport chassis
        root@ying:~> omreport storage  controller
        root@ying:~> omreport storage  battery controller=0
        root@ying:~> omreport system summary
-http://support.dell.com/support/edocs/software/svradmin/5.1/en/omss_ug/html/cli.html

edit /etc/hosts to respect local network
    127.0.0.1       localhost.localdomain   localhost
    192.168.0.100   server1.example.com     server1

    # The following lines are desirable for IPv6 capable hosts
    ::1     localhost ip6-localhost ip6-loopback
    fe00::0 ip6-localnet
    ff00::0 ip6-mcastprefix
    ff02::1 ip6-allnodes
    ff02::2 ip6-allrouters
    ff02::3 ip6-allhosts

update hostname
    echo server1.example.com > /etc/hostname
    /etc/init.d/hostname.sh start
    #may need to restart the system depending on OS version
    hostname
    hostname -f

upgrade OS
    aptitude update
    aptitude full-upgrade

Make sure you're using good nameservers in /etc/resolv.conf (I like to change them to opendns)

Install/Configure Advanced Policy Firewall

install rcconf to handle startup programs

install ntp

install mysql-server mysql-client

install apache

OR install nginx
-adjust log file location for vhosts
-adjust logrotate config file for nginx /etc/logrotate.d/nginx
-install/configure php-fpm

install PHP

Install APC

Install Memcached

install security certificates

install phpmyadmin

install cronolog

install cacti

install rsync

consider mod-evasive (rate limiter for apache)

consider subversion or git if needed.

enable some apache modules if needed
    a2enmod ssl
    a2enmod rewrite

clock
    aptitude install ntp ntpdate

Setup backup job on remote server
