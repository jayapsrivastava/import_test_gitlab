# Run Campaign Storage in VM

Use the 'csbase' box.  If you are far from Hetzner you may want to re-create:
https://gitlab.com/campaignstorage/csbase-bento-packer

Working environments can be obtained easily as follow:

Create a Black Pearl object store BPSim VM
* Download BPsim.ova from http://software.campaignstorage.com/ova/bpsim-3.4-freebsd.ova
* Import this .ova in vmware and start it.  Click retry when VMWare complains about old .ova formats
* Find the IP of the VM on the console displayed by VMWare
* Enter the IP in the file images/vagrant-1vm/config

Get the VMNET and VMNETPREFIX and update the same in Vagrantfile. These values can be obtained -
* For Mac OS - /Library/Preferences/VMware\ Fusion/networking
* For Linux - /etc/vmware/networking

for e.g - VMNET = 2, VMNETPREFIX=10.2.2
```answer VNET_2_DHCP yes
answer VNET_2_DHCP_CFG_HASH B57E323EF23D75491F83BA69CE6738AC3E9B719C
answer VNET_2_HOSTONLY_NETMASK 255.255.255.0
answer VNET_2_HOSTONLY_SUBNET 10.2.2.0
answer VNET_2_VIRTUAL_ADAPTER yes```

Get a working Campaign Storage environment with DS3 object store:

* vagrant up

# Useful information

`vagrant rsync` - sync folder to the guest VM. Path at guest VM `/vagrant`
NOTE : Once folder copied, move it some other location because at reboot or vagrant reload vagrant doesn’t preserve the synced folder.