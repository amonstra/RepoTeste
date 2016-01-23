![logo](https://dl.dropboxusercontent.com/u/97321327/evil/logo.png)
WiFi-Pumpkin
---
[![build](https://travis-ci.org/P0cL4bs/WiFi-Pumpkin.svg)](https://travis-ci.org/P0cL4bs/WiFi-Pumpkin/)

Framework for Rogue Wi-Fi Access Point Attack
### Description
WiFi-Pumpkin is a security tool that provides the Rogue access point to Man-In-The-Middle and network attacks. Purporting to provide wireless Internet services, but snooping on the traffic.
### Installation

Kali 2.0/WifiSlax 4.11.1/Parrot 2.0.5

```sh
 git clone https://github.com/P0cL4bs/WiFi-Pumpkin.git
 cd WiFi-Pumpkin
 chmod +x installer.sh
 ./installer.sh --install
```
refer to the wiki for [Installation](https://github.com/P0cL4bs/WiFi-Pumpkin/wiki/Installation)

### Features
* Rogue Wi-Fi Access Point
* Deauth Attack Clients AP 
* Probe Request Monitor
* DHCP Starvation Attack
* Credentials Monitor
* Transparent Proxy
* Windows Update Attack
* Phishing Manager
* Partial bypass HSTS
* Support beef hook
* Mac Changer 
* ARP Poison 
* DNS Spoof 

### Plugins
- [net-creds](https://github.com/DanMcInerney/net-creds) - Sniff passwords and hashes from an interface or pcap file
- [dns2proxy](https://github.com/LeonardoNve/dns2proxy) - This tools offer a different features for post-explotation once you change the DNS server to a Victim.
- [sslstrip](https://github.com/xtr4nge/sslstrip) - Sslstrip is a MITM tool that implements Moxie Marlinspike's SSL stripping 
attacks by xtr4nge based version

### Transparent Proxy
 Transparent proxies that you can use to intercept and manipulate HTTP traffic modifying requests and responses, that allow to inject javascripts into the targets visited.  You can easily implement a module to inject data into pages creating a python file in directory "Proxy" automatically will be listed on PumpProxy tab.
### Plugins Example
 The following is a sample module that injects some contents into the <head> tag to set blur filter into body html page:
 ``` python
from Plugin import PluginProxy

class blurpage(PluginProxy):
    ''' this module proxy set blur into body page html response'''
    _name          = 'blur_page'
    _activated     = False
    _instance      = None
    _requiresArgs  = False

    @staticmethod
    def getInstance():
        if blurpage._instance is None:
            blurpage._instance = blurpage()
        return blurpage._instance

    def __init__(self):
        self.LoggerInjector()
        self.injection_code = []

    def setInjectionCode(self, code):
        self.injection_code.append(code)

    def inject(self, data, url):
        injection_code = '''<head> <style type="text/css">
        body{
		filter: blur(2px);
		-webkit-filter: blur(2px);}
		</style>'''
        self.logging.info("Injected: %s" % (url))
        return data.replace('<head>',injection_code )

```
 
### Screenshots
![Tool Home](https://dl.dropboxusercontent.com/u/97321327/evil/evil7.3.png)
![Tool demo](https://dl.dropboxusercontent.com/u/97321327/evil/demo7.1.png)
### Issues
Find a bug? Want more features?  Let us know! Please send [file an issue](https://github.com/P0cL4bs/WiFi-Pumpkin/issues/new) 
