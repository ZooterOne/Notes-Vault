```
whois <domain>
```
get domain information.
```
nslookup [-type=<option>] <domain> [<dns>]
```
lookup domain resources.
_Options:_
- `A`_: IPv4_
- `AAAA`_: IPv6_
- `MX`_: email_

_DNS server:_ `1.1.1.1` _(Cloudflare)_ | `8.8.8.8` _(Google)._
```
dnsrecon -t std -d <domain>
```
enumerate DNS records.
```
theHarvester -d <domain> -b bing
```
collect information about domain.
```
dirb http://<domain> <wordlist>
gobuster dir -u http://<domain> -w <wordlist>
ffuf -w <wordlist> -u http://<domain>/FUZZ
ffuf -w <wordlist> -u http://FUZZ.<domain>
```
brute force website directories and sub-domains.

Look for `<domain>/robots.txt` and `<domain>/sitemap.xml`.