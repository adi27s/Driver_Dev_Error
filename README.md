# Device Driver Errors
Personal driver error logs

**1. Install gcc 12**
sudo apt install gcc-12
sudo ln -s -f /usr/bin/gcc-12 /usr/bin/gcc

**2. For Cross Compiler**
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -C /home/aditya/workspace/ldd/source/linux/ M=$PWD modules

cat /home/aditya/.bashrc
copy this line : export PATH=$PATH:/home/aditya/workspace/ldd/downloads/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabihf/bin
paste it in : sudo vi /etc/sudoers file
in -> Defaults secure_path="xyz:export PATH=$PATH:/home/aditya/workspace/ldd/downloads/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabihf/bin"

**3. Ethernet port connection**
Step 1: https://www.youtube.com/watch?v=7gbdNy6XsMc (for ethernet connection)
Step 2: sudo vi /etc/resolv.conf
  Add :
  nameserver 8.8.8.8
  nameserver 8.8.4.4

Step 3: sudo vi /etc/network/interfaces
  Add:
  source /etc/network/interfaces.d/*
  auto lo
  iface lo inet loopback
  
  auto eth0
  iface eth0 inet dhcp
  
  iface usb0 inet static
          address 192.168.7.2
          netmask 255.255.255.252
          network 192.168.7.0
          gateway 192.168.7.1
          dns-nameservers 8.8.8.8
          dns-nameservers 8.8.4.4

Step 4: (not req--test pinging to host pc)
  Default gateway: ip route | grep default
  sudo route add default gw 10.42.0.1 eth0
  
**4.**
