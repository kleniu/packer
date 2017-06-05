# packer
1. Create three host only networks.
'''
VBoxManage hostonlyif create
VBoxManage hostonlyif create
VBoxManage hostonlyif create
'''
check the status:
'''
VBoxManage list hostonlyifs
'''
2. Configure newly created networks
'''
VBoxManage hostonlyif ipconfig vboxnet1 --ip 192.168.101.1 --netmask 255.255.255.0
VBoxManage hostonlyif ipconfig vboxnet2 --ip 192.168.102.1 --netmask 255.255.255.0
VBoxManage hostonlyif ipconfig vboxnet3 --ip 192.168.103.1 --netmask 255.255.255.0
'''
check the status:
'''
VBoxManage list hostonlyifs
'''
3. Import OVA
'''
VBoxManage import ../output-centos/centos.7-docker.ova
'''
output:
'''
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Interpreting /Users/Robert/Development/PACKER/packer/output-centos/centos.7-docker.ova...
OK.
Disks:
  vmdisk1	10737418240	-1	http://www.vmware.com/interfaces/specifications/vmdk.html#streamOptimized	centos.7-docker-disk001.vmdk	-1	-1	

Virtual system 0:
 0: Suggested OS type: "RedHat_64"
    (change with "--vsys 0 --ostype <type>"; use "list ostypes" to list all possible values)
 1: Suggested VM name "centos.7-docker"
    (change with "--vsys 0 --vmname <name>")
 2: Number of CPUs: 2
    (change with "--vsys 0 --cpus <n>")
 3: Guest memory: 2048 MB
    (change with "--vsys 0 --memory <MB>")
 4: Network adapter: orig NAT, config 3, extra slot=0;type=NAT
 5: IDE controller, type PIIX4
    (disable with "--vsys 0 --unit 5 --ignore")
 6: IDE controller, type PIIX4
    (disable with "--vsys 0 --unit 6 --ignore")
 7: Hard disk image: source image=centos.7-docker-disk001.vmdk, target path=/Users/Robert/VirtualBox VMs/centos.7-docker/centos.7-docker-disk001.vmdk, controller=5;channel=0
    (change target path with "--vsys 0 --unit 7 --disk path";
    disable with "--vsys 0 --unit 7 --ignore")
0%...10%...20%...30%...40%...50%...60%...70%...80%...90%...100%
Successfully imported the appliance.
'''