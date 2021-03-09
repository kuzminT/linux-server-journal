- [Securing the SSH service](https://community.hetzner.com/tutorials/securing-ssh) - This article deals with securing the SSH service on Linux systems.

Move db directory to volume:

	/etc/init.d/mysql stop
	mkdir -p /mnt/ext4/MariaDB/
	cp -R /var/lib/mysql/* /mnt/ext4/MariaDB/
	chown -R mysql:mysql /mnt/ext4/MariaDB/*
	vim /etc/mysql/mariadb.cnf
	# Add to the last line:
	datadir = /mnt/ext4/MariaDB

All subsequent changes in the SSH configuration file refer to the following file: `/etc/ssh/sshd_config`.

## Resize volumes
- [Resize volumes](https://community.hetzner.com/tutorials/resize-ext-partition/ru) - official manual
- [Resizing Hetzner Cloud Block Storage Volumes on the Fly](https://blog.ruanbekker.com/blog/2018/12/19/resizing-hetzner-cloud-block-storage-volumes-on-the-fly/)

		# format volume to ext4
		umount /dev/sdaX
		sudo mkfs.ext4 /dev/sdaX
		# Create a new partition
		sudo fdisk /dev/sdaX

## Move postgres data directory

- [ПЕРЕМЕЩЕНИЕ КАТАЛОГА ДАННЫХ POSTGRESQL В UBUNTU 16.04](https://www.8host.com/blog/peremeshhenie-kataloga-dannyx-postgresql-v-ubuntu-16-04/)

After all that steps run `sudo usermod --home '/new/path/todirectory' postgres` and then start postgres.

## SSH User

- [How to Create an SFTP User with Limited Access on Ubuntu](https://wisdmlabs.com/blog/create-an-sftp-user-with-limited-access-on-ubuntu/)

		# Add new group
		sudo groupadd mynewgroup

		# Add an Existing User Account to a Group
		usermod -a -G examplegroup exampleusername
		