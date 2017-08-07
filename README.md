Website Address: http://52.37.173.59/

## Steps as described in Udacity project description:

### Created SSH key
### Created a new user account 'grader'
### Created ssh login using ssh key (no username/password required)
### Change the SSH port from 22 to 2200
### Configured the Uncomplicated Firewall (UFW) to allow SSH ports and ports listed in project description
### Configured the local timezone to UTC
### Installed and configured Apache2 for Python mod_wsgi application
### Installed PostgreSQL
### Configured PostgreSQL with new database 'catalog' and new user 'catalog' with PASSWORD=password
### Installed git
### Cloned and configured Udacity RenoTrack project (/var/www/Renotrack)
### Installed RenoTrack Dependencies
### Configured and Enabled a new Apache Configuration file (/etc/apache2/sites-available/RenoTrack.conf)
	```
	<VirtualHost *:80>
		ServerName 52.37.173.59
		ServerAdmin allenwrench@gmail.com
		WSGIScriptAlias / /var/www/html/RenoTrack/RenoTrack.wsgi
		<Directory /var/www/html/RenoTrack/RenoTrack/>
			Order allow,deny
			Allow from all
		</Directory>
		Alias /static /var/www/html/RenoTrack/RenoTrack/static
		<Directory /var/www/html/RenoTrack/RenoTrack/static/>
			Order allow,deny
			Allow from all
		</Directory>
		ErrorLog ${APACHE_LOG_DIR}/error.log
		LogLevel warn
		CustomLog ${APACHE_LOG_DIR}/access.log combined
	</VirtualHost>
	```

### Created .wsgi File to run python application (/var/www/RenoTrack/RenoTrack.wsgi)
	```
	#!/usr/bin/python
	import sys
	import logging
	logging.basicConfig(stream=sys.stderr)
	sys.path.insert(0,"/var/www/FlaskApp/")

	from FlaskApp import app as application
	application.secret_key = 'Add your secret key'
	```
### Restarted Apache service

## 3rd Party Tutorials:
https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

## Software Installed
*Apache2
*PostgreSQL
*bleach
*git
*github-flask
*httplib2
*libapache2-mod-wsgi
*oauth2client
*python-flask
*python-pip
*python-psycopg2
*python-sqlalchemy
*requests
