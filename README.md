# StrongSwan IKEv2 VPN setup with IBM Kubernetes Service


IBM Cloud Kubernetes service --> initial connection to on-prem Strong Swan IPSEC

Hey There

This repo a couple of scripts (and those are perfect manuals at the same time) that lets you deploy a VPN server in a matter of minutes.
It requires a fresh `Ubuntu 16.04`

You're welcome to browse the `.sh` files and hack your own out of those, or just use the commands below to quickly get the job done.

These scripts are based on this cool tutorial article: https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ikev2-vpn-server-with-strongswan-on-ubuntu-16-04 (thanks DigitalOcean!)

### Deploy with Pre Shared Key auth

This script would uuidgen a PSK and print it out to console, where you can copy and hit enter to continue.

After you `ssh your_vpn_machine`, just run this: 
```
curl -L https://raw.githubusercontent.com/ahmadsayed/ikev2_vpn/master/ikev2-deploy-psk.sh -o ~/deploy.sh 

#Edit the deploy.sh and update leftsubnet, with softlayer private subnet
chmod +x ~/deploy.sh && ~/deploy.sh
```
---
### Deploy Strongswan on IBM Cloud kubernetes Service
after starting your cluster run the following command 
download config.yaml file, and update the following
remote.gateway with softlayer public IP
remote.subnet with softlayer private subnet
privateIPtoPing with Softlayer machine private IP

helm install -f config.yaml --name=vpn ibm/strongswan


Please feel free to open an issue or drop me a pull request.

Bogdan (Dan) Pashchenko
https://ios-engineer.com
