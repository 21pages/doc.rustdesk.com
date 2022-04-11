---
title: Installation 
weight: 10
---

## Set up your own cloud by following simple steps
-----------

### STEP-1 : Download server-side software programs

[Download](https://github.com/rustdesk/rustdesk-server/) or use docker rustdesk/rustdesk-server, **Note:** You need [buy license](https://rustdesk.com/server/) When using this software

Three platform versions provided:
  - Linux
  - Windows

Below tutorial is based on Linux build.

There are two executables:
  - hbbs - RustDesk ID/Rendezvous server
  - hbbr - RustDesk relay server

They are built on Centos7, tested on Centos7/8, Ubuntu 18/20.

### STEP-2 : Run hbbs and hbbr on server

Run hbbs/hbbr on your server (Centos or Ubuntu). We suggust you use [pm2](https://pm2.keymetrics.io/) managing your service.

By default, hbbs listens on 21115(tcp) and 21116(tcp/udp), hbbr listens on 21117(tcp). Be sure to open these ports in the firewall.

- TCP(21115, 21116, 21117)
- UDP(21116)

Please run with "-h" option to see help if you wanna choose your own port.

#### Docker example
```
sudo docker image pull rustdesk/rustdesk-server
sudo docker run --name hbbr -p 21117:21117 -v `pwd`:/root -it --rm rustdesk/rustdesk-server hbbr -m <registered_email>
sudo docker run --name hbbs -p 21115:21115 -p 21116:21116 -p 21116:21116/udp -v `pwd`:/root -it --rm rustdesk/rustdesk-server hbbs -r <relay-server-ip> -m <registered_email>
```
- Note: If you wish to host the server on your own for demonstration or testing purposes, you can specificy `demo` within the `<registered_email>` flag. This will allow your server to run for 30 days.


### STEP-3 : Set hbbs/hbbr address on client-side

Click on menu button on the right side of ID as below, choose "ID/Relay Server".

![](/docs/en/self-host/install/images/server-set-menu.png)

Please input hbbs host or ip address in ID server input box on remote and local side, and hbbr host or ip address in relay server input box on remote side.

e.g.

```
hbbs.yourhost.com
hbbr.yourhost.com
```

or

```
hbbs.yourhost.com:21116
hbbr.yourhost.com:21117
```

![](/docs/en/self-host/install/images/server-set-window.png)