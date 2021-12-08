# t3website2

(Replace MYSITE with your new sitename.)

## How to set up?
- git clone https://github.com/nvsx/t3website2.git
- mv t3website2 MYSITE
- cd MYSITE
- rm -r .git
- ddev config
	- (name: MYSITE)
	- (docroot: public)
	- (project type: typo3)
- ddev start
- ddev composer install
- open https://MYSITE.ddev.site/typo3

This will show an error, because there is no data in the database yet. 

- import database: 
```$ ddev import-db --src Build/Data/dbdump.sql```
- Login with test_admin:test_admin

- In Backend adjust site configuration:
- Module: Sites, select Home
- "Entry Point": Adjust to https://MYSITE.ddev.site
- "Site Identifier": Set to MYSITE
- Save and Close
- open Homepage: https://MYSITE.ddev.site/

### Recover if database is missing
We can setup the database via
https://t3website2.ddev.site/typo3/install.php
and creating a file with
touch public/typo3conf/ENABLE_INSTALL_TOOL
Then set a new install password ("test_admin") and enter the backend. 
Here we need to run the "ANALYZE DATABASE" task and create the missing tables. 
Use "CREATE ADMINISTRATOR" to create a super user, so you can log in later.

### Export database and files
```
$ ddev export-db --gzip=false --file Build/Data/dbdump.sql
$ tar -cvzf Build/Data/fileadmin.tar.gz public/fileadmin
```

### Import databyse and files
```
$ ddev import-db --src Build/Data/dbdump.sql
$ tar -xvzf Build/Data/fileadmin.tar.gz
```

## Configuring a new project
- Add Logo
- Add favicon.ico and other icons
- Install required additional extensions

## Select TYPO3 composer packages
- https://get.typo3.org/misc/composer/helper

***
