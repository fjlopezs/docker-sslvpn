 SSLVPN All In One Docker Image: `baselibrary/sslvpn`
=========

Package common SSLVPN client, automatic VPN connection settings and enable the SSH and Socks 5 proxy.

[![](http://dockeri.co/image/baselibrary/sslvpn)](https://registry.hub.docker.com/u/baselibrary/sslvpn/)

## Supported TAGS
- `latest`
- `1.0`   

## how to use
### Start an instance
    
    docker run -d \
      --device /dev/ppp \
      --cap-add=NET_ADMIN \
      -e VPN_TYPE=fortinet \
      -e VPN_HOST=IP \
      -e VPN_PORT=10443
      -e VPN_USER=username \
      -e VPN_PASS=password \
      baselibrary/sslvpn:1.0

## Environment Variables
### VPN_TYPE
Currently supports the following two types of VPN vendors

- `fortinet`
- `openvpn`

### VPN_HOST
>Applicable VPN type:Forticlient, OpenVPN

Address of the remote VPN server

### VPN_USER
>Applicable VPN type:Forticlient, OpenVPN

Connecting VPN account username

### VPN_PASS
>Applicable VPN type:Forticlient, OpenVPN

VPN connection account password

### VPN_SEED
>Applicable VPN Type: OpenVPN

If you are using `Google Authenticator` authentication mode, set 16 seeds

### VPN_ROUTE
>Applicable VPN type:Forticlient, OpenVPN

If you need a custom VPN connection route by setting VPN_ROUTE needs to be routed to the source address, such as: `10.138.111.0/255.255.255.0`

### VPN_CA
>Applicable VPN Type: OpenVPN

OpenVPN CA certificate.

### VPN_CLIENT_CERT
>Applicable VPN Type: OpenVPN

OpenVPN client \ user certificates.

### VPN_CLIENT_KEY
>Applicable VPN Type: OpenVPN

OpenVPN client \ KEY user certificates.

### VPN_TLS_AUTH
>Applicable VPN Type: OpenVPN

OpenVPN TLS auth key.

### VPN_TRUSTED_CERT
>Applicable VPN Type: Fortinet

Fortinet VPN trusted certificate sha signature.

### SSH_PORT
>Applicable VPN type:Forticlient, OpenVPN

SSH port default 20022.

### SSH_PASS
>Applicable VPN type:Forticlient, OpenVPN

SSH password is empty by default, not set.

### AUTHORIZED_KEYS
>Applicable VPN type:Forticlient, OpenVPN

SSH's AUTHORIZED KEYS, empty by default, not set.

### SOCK_PORT
>Applicable VPN type:Forticlient, OpenVPN

SOCK proxy port default 10080.

### SOCK_PASS
>Applicable VPN type:Forticlient, OpenVPN

SOCK proxy password is empty by default, not set.


 
## Note


+ SSLVPN need to mount the appropriate device:
   OpenVPN need to mount `/dev/net/tun`
   Fortinet need to mount `/dev/ppp`
+ Examples of container must start to set up the network management authority, using the following parameters:
   `--cap-add=NET_ADMIN`
+ Fortinet's VPN using the ppp protocol, requires the use of host network
+ SSH can be changed through the environment variable-related settings, if you do not set any SSH related variables, SSH service is not started by default
 
