---
layout: default
title: Cheatsheet
parent: Linux
nav_order: 3
---

# Cheatsheet

___

## enable Wake on Lan

Add in /etc/network/interfaces
```
_post-up /usr/sbin/ethtool -s eno1 wol g_
```

___

## Process mem usage in Mb
```
ps aux | awk '{print $6/1024 " MB\t\t" $11}' | sort -n
```

___

## remove null from exp results in jq
```
jq '<expression> | select(.Timestamp != null)
```

___

## import CA certificate in a snap (mandatory for bitwarden client)
```
certutil -d /path/to/snap/.pki/nssdb -A -t "TC,," -n "CA name" -i /path/to/cert
```

___

## Banalize template
```
test $EUID -eq 0 || { echo "Run this script as root"; exit 1; }

package-cleanup --oldkernels --count=1

logrotate -f /etc/logrotate.conf
rm -f /var/log/*-???????? /var/log/*.gz
rm -f /var/log/dmesg.old
rm -rf /var/log/anaconda

cat /dev/null > /var/log/audit/audit.log
cat /dev/null > /var/log/wtmp
cat /dev/null > /var/log/lastlog
cat /dev/null > /var/log/grubby

rm -rf /etc/ssh/*key*

sed -i 's/HOSTNAME=.*$/HOSTNAME=localhost/g' /etc/sysconfig/network
echo 'localhost' > /etc/hostname

find /etc/sysconfig/network-scripts -name ifcfg-* | while read cfg;do
  sed -i -e '/^HWADDR=/d' -e '/^UUID=/d' -e 's/^IPADDR=/#IPADDR=/g' $cfg
done

rm -f /etc/udev/rules.d/*-persistent-*.rules
rm -f /var/lib/dbus/machine-id
echo "uninitialized" > /etc/matchine-id
rm -f /etc/yum.repo.d/*.repo

yum clean all

rm -f /root/.bash_history

touch /.unconfigured

history -c

*For RHEL, add :*
subscription-manager remove --all
subscription-manager unregister
subscription-manager clean
```
<sub>source: https://lofic.github.io/tips/linux-banalize.html</sub>

___

## find files in date range, copy them to another folder
```
find -newerct "3 May 2024" ! -newerct "4 May 2024" | xargs cp -t ~/test
```

___

## Encrypt/descrypt with openssl
```
openssl enc -aes-256-cbc -pbkdf2 -pass pass:mypass -in myfile -out encrypted
```
```
openssl enc -aes-256-cbc -pbkdf2 -pass pass:mypass -d -in encrypted -out decrypted
```
