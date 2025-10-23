# Filter

URL Inc Regex: `.*WebGoat.*`
URL Exc Regex: `.*lesson.*.mvc.*`

# Breakpoint

Location: `RequestHeader`
Match: `Contains`
String `Post`

# Proxy to HTTPS

`Tools | Options | Network | Server Certificates` and hit `Generate`. Then import the certificate to the web browser.

# Manually setting the proxy

Edit `/etc/hosts` and add `127.0.0.1 self.internal`.
Configure manual proxy from `Settings | Network Settings` using `self.internal` and configured ZAP port.
