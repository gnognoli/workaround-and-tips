# How to install latest ruby with latest ssl lib  on ubuntu using rbenv

#1 git clone https://github.com/rbenv/rbenv.git ~/.rbenv

#2 echo 'eval "$(~/.rbenv/bin/rbenv init - bash)"' >> ~/.bashrc

#3 RUBY_CONFIGURE_OPTS=--with-openssl-dir=/usr/lib/ssl rbenv install 3.1.2

#4 rbenv global 3.1.2

#5 exit from your current shell session and reconnect, you should be able to use  the ruby version you newly installed

# How to run virtualbox after server reboot or server crash

#1 check vbox driver service is started without issue 
```sh
systemctl status vboxdrv
```
result should be 
```sh
root@ns3066876:~# systemctl status vboxdrv
● vboxdrv.service - VirtualBox Linux kernel module
   Loaded: loaded (/usr/lib/virtualbox/vboxdrv.sh; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2024-04-08 01:59:26 GMT; 5s ago
  Process: 11255 ExecStop=/usr/lib/virtualbox/vboxdrv.sh stop (code=exited, status=0/SUCCESS)
  Process: 11296 ExecStart=/usr/lib/virtualbox/vboxdrv.sh start (code=exited, status=0/SUCCESS)

Apr 08 01:58:51 ns3066876 systemd[1]: Starting VirtualBox Linux kernel module...
Apr 08 01:58:51 ns3066876 vboxdrv.sh[11296]: vboxdrv.sh: Starting VirtualBox services.
Apr 08 01:58:51 ns3066876 vboxdrv.sh[11326]: Starting VirtualBox services.
Apr 08 01:58:51 ns3066876 vboxdrv.sh[11296]: vboxdrv.sh: Building VirtualBox kernel modules.
Apr 08 01:58:51 ns3066876 vboxdrv.sh[11333]: Building VirtualBox kernel modules.
Apr 08 01:59:25 ns3066876 vboxdrv.sh[16431]: VirtualBox kernel modules built.
Apr 08 01:59:26 ns3066876 vboxdrv.sh[16450]: VirtualBox services started.
Apr 08 01:59:26 ns3066876 systemd[1]: Started VirtualBox Linux kernel module.
```

If you have Kernel module is not loaded, then restart vboxdrv service, this could take a while, be patient
```sh
systemctl restart vboxdrv
```
Then start or restart vboxweb-service
```sh
sudo systemctl restart vboxweb-service
```
Check the vboxweb-service status
```sh
sudo systemctl status vboxweb-service
```
The result should be 
```sh
root@ns3066876:~# sudo systemctl status vboxweb-service
● vboxweb-service.service
   Loaded: loaded (/usr/lib/virtualbox/vboxweb-service.sh; enabled; vendor preset: enabled)
   Active: active (exited) since Mon 2024-04-08 01:59:51 GMT; 3s ago
  Process: 16468 ExecStop=/usr/lib/virtualbox/vboxweb-service.sh stop (code=exited, status=0/SUCCESS)
  Process: 16482 ExecStart=/usr/lib/virtualbox/vboxweb-service.sh start (code=exited, status=0/SUCCESS)

Apr 08 01:59:51 ns3066876 systemd[1]: Starting vboxweb-service.service...
Apr 08 01:59:51 ns3066876 vboxweb-service.sh[16482]: vboxweb-service.sh: Starting VirtualBox web service.
Apr 08 01:59:51 ns3066876 vboxweb-service.sh[16493]: Starting VirtualBox web service.
Apr 08 01:59:51 ns3066876 vboxweb-service.sh[16512]: VirtualBox web service started.
Apr 08 01:59:51 ns3066876 systemd[1]: Started vboxweb-service.service.
root@ns3066876:~# screen -x
[detached from 4800.pts-0.ns3066876]
[detached from 4800.pts-0.ns3066876]
```
#2 The most important and vicious part is to be careful to start phpvirtualbox using the right user account (run it in a screen if you did not daemonized it) : 
```sh
micky@ns3066876:~$ vboxwebsrv
```

# How to run Jasmin UI, py4web after server restart

#1
```
$ cd /opt
$ python3 -m venv py4web
```
#2 Activate the virtual environment
```
$ source py4web/bin/activate
```
#3 Run the server 
```
py4web run apps --host 0.0.0.0
```

# Debug smpp with tcpdump wireshark
#1 capture packets
```
/usr/sbin/tcpdump -v -i any -w /opt/file-name-102.176.160.207-8.pcap net 102.176.160.207 -s 0
```
#2 use wireshark to analyse pcap file

# How to decode and encode jasmin smpp pdu
```
https://github.com/jookies/smpp.pdu
```
# WARN - attack prevented by Rack::Protection::AuthenticityToken (Sinatra, Padrino)

Allow developper to disable protect_from_csrf for some traversal path

#2 config/apps.rb
```
set :protection, true
set :protect_from_csrf, true
set :allow_disabled_csrf, true
```

#2 controller
```post :payment, :csrf_protection => false  do
  end
```

