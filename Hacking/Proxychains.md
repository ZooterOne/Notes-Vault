### Installation
```
sudo apt install proxychains
```
install proxychains.
```
sudo nano /etc/proxychains.conf
```
edit proxychains configuration.
___
### Use free proxies
edit proxychains.conf as follows:
- _comment strict\_chain out_.
- _enable dynamic\_chain_.
- _find proxy addresses from_ [Proxy list](https://spys.one/en/).
___
### Use tor
```
sudo apt install tor
sudo systemctl enable tor.service
sudo systemctl start tor.service
sudo systemctl status tor.service
```
install tor service.
edit proxychains.conf as follows:
- _comment strict_chain out_.
- _enable dynamic_chain_.
- _enable tor proxies socks4 and socks5_.
```
service tor start
service tor stop
service tor status
```
alternative commands to start, stop or check tor service.
___
### Run command
```
proxychains <command>
```
run command through proxychains.