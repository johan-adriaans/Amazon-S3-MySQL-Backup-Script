Amazon-S3-MySQL-Backup-Script
=============================

A port of the popular http://sourceforge.net/projects/automysqlbackup/ script. This version dumps and compresses these dumps in a tmp folder and moves the compressed archives to Amazon S3.

Configuration
=============
Step 1:
-------
Make sure you have s3cmd installed and configured (http://s3tools.org/s3cmd). s3cmd is available as a package for all major Linux distro's.
- Ubuntu: sudo apt-get install s3cmd
- CentOS/RHEL: yum install s3cmd
- SUSE Linux Enterprise Server 11: # zypper addrepo http://s3tools.org/repo/SLES_11/s3tools.repo ; zypper install s3cmd

After the installation you should run: s3cmd --configure
More information here: http://s3tools.org/s3cmd-howto

Step 2:
-------
Edit the automysqlbackup.s3 file and set the BACKUPDIR to an existing bucket (or create the mysql_backups bucket using: s3cmd mb s3://mysql_backups). On most Debian based hosts the USERNAME and PASSWORD variables are read from /etc/mysql/debian.cnf. On other distro's you should add a read only account to MySQL use those credentials in the script.

Step 3:
-------
Move the script to /etc/cron.daily so it is executed every night. Make sure to set the execute permissions.
