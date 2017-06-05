# packer
1. Create three host only networks.
```
VBoxManage hostonlyif create
VBoxManage hostonlyif create
VBoxManage hostonlyif create
```
check the status:
```
VBoxManage list hostonlyifs
```
2. Configure newly created networks
```
VBoxManage hostonlyif ipconfig vboxnet1 --ip 192.168.101.1 --netmask 255.255.255.0
VBoxManage hostonlyif ipconfig vboxnet2 --ip 192.168.102.1 --netmask 255.255.255.0
VBoxManage hostonlyif ipconfig vboxnet3 --ip 192.168.103.1 --netmask 255.255.255.0
```
check the status:
```
VBoxManage list hostonlyifs
```
3. Import OVA
```
VBoxManage import ../output-centos/centos.7-docker.ova --vsys 0 --vmname docker1 --cpus 1 --memory 1024
VBoxManage modifyvm docker1 --nic2 hostonly --hostonlyadapter2 vboxnet1
VBoxManage startvm docker1
```
4. Configure guest
```
VBoxManage guestcontrol docker1 --username root --password packer run -- /bin/hostnamectl set-hostname docker1
VBoxManage guestcontrol docker1 --username root --password packer run -- /bin/nmcli con mod "Wired connection 1" ipv4.addresses 192.168.101.100/24
VBoxManage guestcontrol docker1 --username root --password packer run -- /bin/nmcli con mod "Wired connection 1" ipv4.method manual
VBoxManage guestcontrol docker1 --username root --password packer run -- /bin/nmcli con mod "Wired connection 1" connection.sutoconnect yes
```
