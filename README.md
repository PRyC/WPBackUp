# WP BackUp Script (WordPress BackUp Script)

BASH script for WordPress site backups with S3 and password support. 

## Required software:
bash, sha512sum, p7zip, p7zip-full, wp-cli, sudo and - optional - s3cmd

## Configure script

```
SITE_DIR - SITE DIR schema, eg.:
SITE_DIR="/var/www/"$SITE"/public_html/"

EXCLUDE - Folders (or files) to be excluded from backup

SPLIT_ARCH - Split tar file
SPLIT_ARCH_SIZE - Split archive size, eg 20M = 20 MB

KEEP_LOCAL - Set 0 to delete the local copy after transfer to S3 (requires an active S3), 1 to keep, eg.:
KEEP_LOCAL=0

UPDATE - Update WP + themes + plugins AFTER full or major backup (1 - yes), eg.:
UPDATE=1

BACKUP2S3 - Set to 1 to activate S3 
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
sudo ./wpbackup SITE TYPE
```
Eg.:

```
# BackuP WordPress databes for example.com site:
sudo ./wpbackup example.com db 

# BackUp Full WordPress for example.com site
sudo ./wpbackup example.com full

# BackUp MAJOR WordPress for example.com site
sudo ./wpbackup example.com major

# Display the password for the archive for example.com site
# PSWD1, PSWD2 and BACKUP_ARCHIVE_PASSWORD
# MASTER PASSWORD for archive (BASE + SHA512)
sudo ./wpbackup example.com pswd

```
Or move/copy to:

```
/usr/local/bin/
```
and run from anywhere:
```
sudo wpbackup SITE TYPE
```

### Remember to set the appropriate attributes for the script file: 
```
sudo chmod +x ./wpbackup
```


## License
[GPL-3.0 License](https://github.com/PRyC/WPBackUp/blob/main/LICENSE)