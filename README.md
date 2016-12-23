# openvpn
[![](https://images.microbadger.com/badges/image/armswarm/openvpn.svg)](https://microbadger.com/images/armswarm/openvpn "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/armswarm/openvpn.svg)](https://microbadger.com/images/armswarm/openvpn "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/commit/armswarm/openvpn.svg)](https://microbadger.com/images/armswarm/openvpn "Get your own commit badge on microbadger.com") [![Build Status](https://drone.veiled.land/api/badges/armswarm/openvpn/status.svg)](https://drone.veiled.land/armswarm/openvpn)

OpenVPN docker image, for ARM.

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
