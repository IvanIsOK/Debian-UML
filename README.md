# Debian-UML
## How do we run debian in an uml?
We need to compile the linux kernel and use the compiled linux binary!, Its easy!

## Compiling 
Download the latest linux source tarball from https://kernel.org/ and untar it.
In the untared folder run these commands:  
### make mrproper
### make ARCH=um defconfig
### make -j19 ARCH=um (replace -j with the number of threads you want to use.)

## Running  
In the kernel dir make the linux binary executable: 
# chmod +x linux
Download the rootfs.img from releases
Then run this command: 
"./linux \
  ubd0=/path/to/your/rootfs.img \
  mem=512M \
  root=/dev/ubda \
  con0=fd:0 \
  systemd.unit=multi-user.target" 
  
  ### It should run a new shell, log in with root and passwd root, it should say some messages about waranty, it will maybe be stuck on that message without giving a shell, wait it should give you one, for me it takes about 30 sec but it could be shorter or longer.
