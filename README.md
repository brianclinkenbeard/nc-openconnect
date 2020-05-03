# nc-openconnect
A shell script to access SSH through a OpenConnect-compatible (e.g. AnyConnect) VPN. This allows for OpenConnect to only handle SSH activity instead of all network traffic on the host, and is useful for networks secured by VPNs.

## Usage
### Requirements
- openconnect
- ocproxy

### Script configuration
Download the script to a folder in your `PATH`. Fill out the necessary fields, and provide the password from plaintext or a keyring:
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

## Acknowledgements
Based off [Martin Monperrus' bash script](https://www.monperrus.net/martin/ssh-over-vpn-with-openconnect). Changes under the ISC license.
