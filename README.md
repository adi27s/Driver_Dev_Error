# Device Driver Errors
Personal driver error logs

**1. Install gcc 12**<br>
sudo apt install gcc-12 <br>
sudo ln -s -f /usr/bin/gcc-12 /usr/bin/gcc <br>

**2. For Cross Compiler**<br>
sudo make ARCH=arm CROSS_COMPILE=arm-linux-gnueabihf- -C /home/aditya/workspace/ldd/source/linux/ M=$PWD modules<br>

cat /home/aditya/.bashrc<br>
copy this line : export PATH=$PATH:/home/aditya/workspace/ldd/downloads/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabihf/bin<br>
paste it in : sudo vi /etc/sudoers file<br>
in -> Defaults secure_path="xyz:export PATH=$PATH:/home/aditya/workspace/ldd/downloads/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabihf/bin"<br>

**3. Ethernet port connection**<br>
Step 1: https://www.youtube.com/watch?v=7gbdNy6XsMc (for ethernet connection)<br>
Step 2: sudo vi /etc/resolv.conf<br>
  Add :<br>
  nameserver 8.8.8.8<br>
  nameserver 8.8.4.4<br>

Step 3: sudo vi /etc/network/interfaces<br>
  Add:<br>
  source /etc/network/interfaces.d/*<br>
  auto lo<br>
  iface lo inet loopback<br>
  
  auto eth0<br>
  iface eth0 inet dhcp<br>
  
  iface usb0 inet static<br>
          address 192.168.7.2<br>
          netmask 255.255.255.252<br>
          network 192.168.7.0<br>
          gateway 192.168.7.1<br>
          dns-nameservers 8.8.8.8<br>
          dns-nameservers 8.8.4.4<br>

Step 4: (if ethernet eth0 ip isnt visible--test pinging to host pc)<br>
  Default gateway: ip route | grep default<br>
  sudo route add default gw 10.42.0.1 eth0<br>
  
**4. In bashrc add path cross compiler**<br>
  export PATH=$PATH:/home/aditya/workspace/ldd/downloads/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabihf/bin

