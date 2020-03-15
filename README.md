# post_loom


#### Software Versions
I'm using `dpdk-stable-17.11.6` which seem to be LTS and used in BESS as the default DPDK. Also the BESS is just the latest commit.

#### Good github issues for BESS
[Issue 1](https://github.com/NetSys/bess/issues/934)

#### Huge page config in the grub
`GRUB_CMDLINE_LINUX_DEFAULT="hugepagesz=2M hugepages=4096 default_hugepagesz=1G hugepagesz=1G hugepages=5"` 

also add the following line in the `/etc/fstab` `nodev /mnt/huge_1GB hugetlbfs pagesize=1GB 0 0`


#### TestPMD Command
`sudo ./build/app/testpmd –l 0-1 –n 4 --vdev="virtio_user0,path=/users/alireza/my_vhost0.sock,queues=1" --log-level=8 --socket-mem 1024,1024 --no-pci -- -i --disable-hw-vlan --total-num-mbufs=1025` 

#### Tas Command
`sudo ./tas/tas --ip-addr=10.0.0.1/24 --fp-cores-max=1 --fp-no-xsumoffload --fp-no-ints --fp-no-autoscale --dpdk-extra=--no-pci --dpdk-extra=--vdev --dpdk-extra=virtio_user0,path=/users/alireza/my_vhost0.sock,queues=1`

