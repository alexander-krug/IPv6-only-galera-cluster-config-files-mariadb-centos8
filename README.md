# How to set up a 3-server MariaDB mirroring setup under CentOS8
This contains working config files for a 3-server MariaDB mirroring setup under CentOS8

## Details of my working setup:

MariaDB: MariaDB 10.3

OS: CentOS8

Kernel release: 4.18.0-147.3.1.el8_1.x86_64



## Follow the Guide from digitalocean with some expections

Original link: https://www.digitalocean.com/community/tutorials/how-to-configure-a-galera-cluster-with-mariadb-on-centos-7-servers

Internet archive link, in case something changes/disappears: https://web.archive.org/web/20230000000000*/https://www.digitalocean.com/community/tutorials/how-to-configure-a-galera-cluster-with-mariadb-on-centos-7-servers



## Here are the exceptions

1. Skip step 1, no need to add the repo

2. Install different packages
```
sudo dnf install mariadb-server
sudo dnf install policycoreutils-python-utils
```

3. The config files for /etc/my.cnf.d/galera.cnf are different for IPv6 only networks, refer to the config files in this repo

4. Verify that the file /usr/lib64/galera-4/libgalera_smm.so exists 
```
ls /usr/lib64/galera-4/libgalera_smm.so
```
If it does not, try to see if /usr/lib64/galera/libgalera_smm.so exists. If so, then either create a symbolic link or change the line in each config file.
To create a symbolic link:
```
ln -s /usr/lib64/galera-4/libgalera_smm.so /usr/lib64/galera-4/libgalera_smm.so
```

