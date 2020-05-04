# nc-openconnect
A shell script to access SSH through a OpenConnect-compatible (e.g. AnyConnect) VPN. This allows for OpenConnect to only handle SSH activity instead of all network traffic on the host, and is useful for networks secured by VPNs.

This works by using `ocproxy` and `nc` to create a SOCKS proxy for the VPN, and then configuring SSH to connect through the proxy.

## Setup
### Requirements
- openconnect
- ocproxy

### Script configuration
[Download the script](https://raw.githubusercontent.com/brianclinkenbeard/nc-openconnect/master/nc-openconnect) to a folder in your `PATH`. Fill out the necessary fields, and provide the password from plaintext or a keyring:
```
USER='bclinkenbeard'
PASSWD_CMD='echo my_pass'
VPN='my.vpn.org'
```

### SSH configuration
Add to `~/.ssh/config`:
```
Host my.vpn.org
	ProxyCommand nc-openconnect %h %p
```

Now, each time you SSH to your host, `nc-openconnect` will authenticate and route your connection through the VPN. The VPN will be disconnected when you exit the shell.

## Acknowledgements
Based off [Martin Monperrus' bash script](https://www.monperrus.net/martin/ssh-over-vpn-with-openconnect). Changes under the ISC license.
