# Ubuntu Linux Laptop Setup

Ubuntu Linux Laptop Setup for Cloud Engineer, DevOps Engineer or Linux Systems Administrator

1. Download Ubuntu Desktop from Canonical:
https://ubuntu.com/#download

2. Register for Ubuntu Pro
https://ubuntu.com/pro

3. Ready the Machine for Virtualization Software (e.g. VMware Workstation 17, etc)

sudo apt-get update && sudo apt-get upgrade -y

sudo apt-get install gcc build-essentials -y

Download VMware Workstation 17
https://www.vmware.com/go/getworkstation-linux

cd Downloads && chmod u+x VMware* && sudo ./VMware*

***Run these commands in your terminal***

openssl req -new -x509 -newkey rsa:2048 -keyout VMWARE17.priv -outform DER -out VMWARE17.der -nodes -days 36500 -subj "/CN=VMWARE/"

sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmmon)

sudo /usr/src/linux-headers-$(uname -r)/scripts/sign-file sha256 ./VMWARE17.priv ./VMWARE17.der $(modinfo -n vmnet)

tail $(modinfo -n vmmon) | grep "Module signature appended"

sudo mokutil --import VMWARE17.der

***After you have finished all of the commands above, you need to reboot your machine and then Enroll MOK (your key) and then reboot again. When you log back in, you will be good to go!***

mokutil --test-key VMWARE17.der

The configurations that will be covered are the following:

- [x] VMware Workstation 17 :+1:

- [X] KVM on Ubuntu 22.04LTS (Free Option and Clunky to Navigate and just plain Ugly) :-1:

- [x] Virtualbox :+1: (Optional)


