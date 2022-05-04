# IPSEC VPN Server

## How to

```
git clone https://github.com/hwdsl2/docker-ipsec-vpn-server hwdsl2/docker-ipsec-vpn-server; cd hwdsl2/docker-ipsec-vpn-server

# Generate strong password
openssl rand -base64 10
# Generate a PSK
openssl rand -base64 16

vim vpn.env

# Add following lines bellow
VPN_USER=user_you_prefer
VPN_PASSWORD=PYhf7Loy/6z7xtc/kcMQKA==
VPN_IPSEC_PSK=mruD7+yL4FqLqLJ5Br9tdw==
VPN_DNS_SRV1=1.1.1.1
VPN_DNS_SRV2=1.0.0.1
```

```
docker run \
    --name ipsec-vpn-server \
    --env-file ./vpn.env \
    --restart=always \
    -v ikev2-vpn-data:/etc/ipsec.d \
    -v /lib/modules:/lib/modules:ro \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -d --privileged \
    hwdsl2/ipsec-vpn-server; 
    
docker logs ipsec-vpn-server
    # Output
    Connect to your new VPN with these details:
    
    Server IP: your_vpn_server_ip
    IPsec PSK: your_ipsec_pre_shared_key
    Username: your_vpn_username
    Password: your_vpn_password
```

## References

* [https://github.com/hwdsl2/docker-ipsec-vpn-server#quick-start](https://github.com/hwdsl2/docker-ipsec-vpn-server#quick-start)
