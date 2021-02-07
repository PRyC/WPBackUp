# WP BackUp Script

BASH script for WordPress site backups with S3 and password support. 

## Required software:
p7zip, p7zip-full, sudo, and - optional - s3cmd

## Configure script

```
SITE_DIR - SITE DIR schema, eg.:
SITE_DIR="/var/www/"$SITE"/public_html/"

BACKUP2S3 - Set to 1 to activate S3 (local copy will be deleted)
BACKUP2S3 - Set to 0 to local copy, eg.:
BACKUP2S3=1

S3CFG - Patch to S3 cfg file, eg:
S3CFG=/root/.s3cfg-oss-wpbackup/.$SITE
for example.com S3 cfg file

PSWD1 - Set BASE PASSWORD for archive (eg. 512 a-z A-Z 0-9)
PSWD2 - Auto generate: SHA512 from site name
BACKUP_ARCHIVE_PASSWORD - MASTER PASSWORD for archive (BASE + SHA512)

BACKUP_MAIN_DIR - Set MAIN working folder, eg:
BACKUP_MAIN_DIR="/backup/"

```

## Usage:

```
sudo wpbackup SITE TYPE
```
Eg.:

```
#BackuP WordPress databes for example.com site:
sudo wpbackup example.com db 

# BackUp Full WordPress for example.com site
sudo wpbackup example.com full

# BackUp MAJOR WordPress for example.com site
sudo wpbackup example.com major

# Display the password for the archive for example.com site
# PSWD1, PSWD2 and BACKUP_ARCHIVE_PASSWORD
# MASTER PASSWORD for archive (BASE + SHA512)
sudo wpbackup example.com pswd

```


## License
[GPL-3.0 License](https://github.com/PRyC/WPBackUp/blob/main/LICENSE)