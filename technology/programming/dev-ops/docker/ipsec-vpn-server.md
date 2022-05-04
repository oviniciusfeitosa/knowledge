# IPSEC VPN Server

## How to

```
sudo apt install network-manager-l2tp-gnome ; \
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

### Connect VPN

1. Go to Settings -> Network -> VPN. Click the **+** button.
2. Select **Layer 2 Tunneling Protocol (L2TP)**.
3. Enter anything you like in the **Name** field.
4. Enter `Your VPN Server IP` for the **Gateway**.
5. Enter `Your VPN Username` for the **User name**.
6. Right-click the **?** in the **Password** field, select **Store the password only for this user**.
7. Enter `Your VPN Password` for the **Password**.
8. Leave the **NT Domain** field blank.
9. Click the **IPsec Settings...** button.
10. Check the **Enable IPsec tunnel to L2TP host** checkbox.
11. Leave the **Gateway ID** field blank.
12. Enter `Your VPN IPsec PSK` for the **Pre-shared key**.
13. Expand the **Advanced** section.
14. Enter `aes128-sha1-modp2048` for the **Phase1 Algorithms**.
15. Enter `aes128-sha1` for the **Phase2 Algorithms**.
16. Click **OK**, then click **Add** to save the VPN connection information.
17. Turn the **VPN** switch ON.

```
# Try this if you can`t connect to VPN

sudo systemctl stop xl2tpd.service
sudo systemctl disable xl2tpd.service
systemctl disable xl2tpd.service
sudo systemctl mask xl2tpd.service
```

Once connected, you can verify that your traffic is being routed properly by [looking up your IP address on Google](https://www.google.com/search?q=my+ip). It should say "Your public IP address is `Your VPN Server IP`".

## References

* [https://github.com/hwdsl2/docker-ipsec-vpn-server#quick-start](https://github.com/hwdsl2/docker-ipsec-vpn-server#quick-start)
