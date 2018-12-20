# StrongSwan IKEv2 VPN setup with IBM Kubernetes Service


IBM Cloud Kubernetes service --> initial connection to on-prem Strong Swan IPSEC

Hey There

This repo a couple of scripts (and those are perfect manuals at the same time) that lets you deploy a VPN server in a matter of minutes.
It requires a fresh `Ubuntu 16.04`

You're welcome to browse the `.sh` files and hack your own out of those, or just use the commands below to quickly get the job done.

These scripts are based on this cool tutorial article: https://www.digitalocean.com/community/tutorials/how-to-set-up-an-ikev2-vpn-server-with-strongswan-on-ubuntu-16-04 (thanks DigitalOcean!)

This Readme edited from the original fork to work with IBM cloud kubentes cluser IBM Cloud softlayer machine


### Deploy with Pre Shared Key auth

This script would uuidgen a PSK and print it out to console, where you can copy and hit enter to continue.

After you `ssh your_vpn_machine`, just run this: 
```
curl -L https://raw.githubusercontent.com/ahmadsayed/ikev2_vpn/master/ikev2-deploy-psk.sh -o ~/deploy.sh 

#Edit the deploy.sh and update the following 
# leftsubnet, with softlayer private subnet
# rightsubnet, append IKS workernodes private subnet
chmod +x ~/deploy.sh && ~/deploy.sh
```
---
### Deploy Strongswan on IBM Cloud kubernetes Service

after starting your cluster run the following command 
download config.yaml file, and update the following
remote.gateway with softlayer public IP
remote.subnet with softlayer private subnet
local.subnet append IKS worker node private subnet
privateIPtoPing with Softlayer machine private IP

```
helm install -f config.yaml --name=vpn ibm/strongswan
```
For detailes steps and trouble shooting follow the below URL
https://console.bluemix.net/docs/containers/cs_vpn.html#vpn

