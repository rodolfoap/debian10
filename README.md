# README

1. Get the last image here: https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/ and prepare the USB stick:
```
SOURCE=debian-10.8.0-amd64-netinst.iso
TARGET=/dev/sda

wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/$SOURCE
sudo dd if=$SOURCE of=$TARGET bs=4M
```

2. Install the distro:
```
Encryption:	Whole disk, LVM
Options: 	[x] LXDE
		[x] SSHServer
		[x] Standard-system-utilities
```

3. Boot and setup the minimum required:
```
su -
apt update
apt -y install mc git git-crypt pinentry-tty neovim ccrypt mcrypt
update-alternatives --set pinentry /usr/bin/pinentry-tty
git config --global user.name "RodolfoAP"
git config --global user.email rodolfoap@gmail.com
git clone https://github.com/rodolfoap/debian10.git
cd debian10
chown -R root: pre/{etc,root}
rsync -va pre/ /
grep -q helpers /home/rodolfoap/.bashrc || { echo '. .bashrc_helpers' >> /home/rodolfoap/.bashrc; echo '. .bashrc_helpers' >> /root/.bashrc; }
```

4. Restore all necessary keys, and then, as a normal user:
```
mkdir git
cd git
git clone git@github.com:rodolfoap/debian10.git
```

5. Continue with the sequence listed in the `prc/` directory
6. `dat/` includes some scripts meant to finish the install. Run them as required.
