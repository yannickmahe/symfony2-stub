Symfony2 Stub
=============

The objective is to have a "get started" repo for new projects.

Included
--------

* Symfony2
* Symfony2 vendors (doctrine, twig, assetic...)
* Bootstrap (via git submodule)
* Font Awesome (extra bootstrap icons, via submodule)
* Less.js (asset in common bundle)
* JQuery (via google CDN)

How to install
--------------

* git clone

   git clone --recursive git@github.com:yannickmahe/symfony2-stub.git

* copy parameters.yml.dist to parameters.yml

    cp app/config/parameters.yml.dist app/config/parameters.yml

* init vendors

	composer.phar install

* setup assets for dev

	php app/console assets:install --symlink

* clear cache

	php app/console cache:clear
	php app/console cache:clear --env=prod

* setup host file

	127.0.0.1 	domain.tld

* setup apache

	````
	<VirtualHost *:80>
	    ServerName domain.tld

	    DocumentRoot {{dir}}
	    <Directory {{dir}}>
	        Options Indexes FollowSymLinks MultiViews
	        AllowOverride None
	        Order allow,deny
	        allow from all
	        <IfModule mod_rewrite.c>
	            RewriteEngine On
	            RewriteCond %{REQUEST_FILENAME} !-f
	            RewriteRule ^(.*)$ /app.php [QSA,L]
	        </IfModule>
	    </Directory>
	</VirtualHost>
	````

* restart apache

	sudo service apache2 restart

* Rename the Yannick bundle

