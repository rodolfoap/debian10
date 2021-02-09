# README

1. Get the last image here: https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/ and prepare the USB stick:

```
SOURCE=debian-10.8.0-amd64-netinst.iso
TARGET=/dev/sda

wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/$SOURCE
sudo dd if=$SOURCE of=$TARGET bs=4M
```

2. Install the distro:

Encryption:	Whole disk, LVM
Options: 	[x] LXDE
		[x] SSHServer
		[x] Standard-system-utilities

3. Boot and setup the minimum required:
```
su -
apt update
apt -y install mc git git-crypt pinentry-tty
update-alternatives --set pinentry /usr/bin/pinentry-tty
git clone git@github.com:rodolfoap/debian10.git
cd debian10
rsync -va pre/ /
echo '. .bashrc_helpers' >> /home/rodolfoap/.bashrc
echo '. .bashrc_helpers' >> /root/.bashrc
```

4. Continue with the sequence listed in the `prc/` directory

5. `dat/` includes some scripts meant to finish the install. Run them as required.
