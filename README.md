# My "hosts" file for Windows
Unified hosts with bloked fakenews, gambling, porn, social and some ukrainian popular sites (mostly for work :D ).

## Location of your hosts file
To modify your current `hosts` file, look for it in the following places and modify it with a text
editor.

**Mac OS X, iOS, Android, Linux**: `/etc/hosts` folder.

**Windows**: `%SystemRoot%\system32\drivers\etc\hosts` folder.

## Reloading hosts file
Your operating system will cache DNS lookups. You can either reboot or run the following commands to
manually flush your DNS cache once the new hosts file is in place.

| The Google Chrome browser may require manually cleaning up its DNS Cache on `chrome://net-internals/#dns` page to thereafter see the changes in your hosts file. See: https://superuser.com/questions/723703
:-----------------------------------------------------------------------------------------

### Windows

Open a command prompt with administrator privileges and run this command:

```
ipconfig /flushdns
```

|If you want to use a huge hosts file by merging [hphosts](https://www.hosts-file.net) (NOT INCLUDED HERE) you need to DISABLE and STOP `Dnscache` service before you replace hosts file in Windows Systems. You have been warned.|
:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Before flushing the DNS cache, open a command prompt with administrator privileges and run this command:

```
sc config "Dnscache" start= disabled
sc stop "Dnscache"
```

### Linux

Open a Terminal and run with root privileges:

**Debian/Ubuntu** `sudo service network-manager restart`

**Linux Mint** `sudo /etc/init.d/dns-clean start`

**Linux with systemd**: `sudo systemctl restart network.service`

**Fedora Linux**: `sudo systemctl restart NetworkManager.service`

**Arch Linux/Manjaro with Network Manager**: `sudo systemctl restart NetworkManager.service`

**Arch Linux/Manjaro with Wicd**: `sudo systemctl restart wicd.service`

**RHEL/Centos**: `sudo /etc/init.d/network restart`

**FreeBSD**: `sudo service nscd restart`

To enable the `nscd` daemon initially, it is recommended that you run the following commands:

```
sudo sysrc nscd_enable="YES"
sudo service nscd start
```

Then modify the `hosts` line in your `/etc/nsswitch.conf` file to the following:

```
hosts: cache files dns
```
