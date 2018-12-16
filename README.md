# openvpn

---
**NOTE:**

**This repository has been archived. It has not been update for quite some time and there is no intention of maintaining it.
Please use a different image.**

---

[![Docker Repository on Quay](https://quay.io/repository/armswarm/openvpn/status "Docker Repository on Quay")](https://quay.io/repository/armswarm/openvpn)

This repository builds the openvpn image for ARM.


To run the container:
```
docker run -d \
    --name openvpn \
    -p 1194:1194/udp \
    --cap-add=NET_ADMIN \
    --device=/dev/net/tun \
    -v ${PWD}/secrets:/etc/openvpn/secrets \
    -e CA_ORG="Example Organisation" \
    -e SERVER_NAME="openvpn.example.com" \
    -e OPENVPN_LINKED_SUBNET=192.168.1.0 \
    openvpn
```

To get configuration for a new client (it will be saved as an archive with the other secrets on the host path):

```
docker exec -it openvpn sh -c 'cd /etc/openvpn/secrets && KEY_SIZE=4096 new-client-cert example'
```
