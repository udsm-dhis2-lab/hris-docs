.. installation:

********************
Installation Manual
********************

**Eclipse Plugins:**

Yedit ( Eclipse plugin for YAML Files - http://code.google.com/p/yedit/)
	update site: http://dadacoalition.org/yedit
Symfony Eclipse Plugin ( https://github.com/pulse00/Symfony-2-Eclipse-Plugin )
	update site: http://p2.dubture.com


**Configurations:**

    * Setting Date time Zone
	- Set date time zone inside php.ini to:

	- date.timezone = 'Africa/Dar_es_Salaam'

    * Turn off short_open_tag
	- Disable detection of PHP codes between <? and ?> for better PHP >=5.3 Experience

	- Set it inside php.ini to: short_open_tag = Off

    * Give Web readwrite access to cache and log directory in your SymfonyProject
	- To enjoy both user and web read-write access in linux use the following commands:
		cd SymfonyProject/

		rm -rf app/cache/*

		rm -rf app/logs/*

	- On Systems supporting chmod +a
		sudo chmod +a "www-data allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs

		sudo chmod +a "`whoami` allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs

	- On Systems that don't support chmod +a
		sudo setfacl -R -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs

		sudo setfacl -dR -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs

	- On Systems that doesn't support either
		sudo chown youruseraccount:www-data cache/ logs/ config/parameters.yml -R

    * Database Configurations
	- HRHIS Makes use of postgres set the configurations accordingly

		+ Driver: PostgreSQL(PDO) "pdo_pgsql"

		+ Username: databaseusername "hris"

		+ Password: userpassword "hris"
 
		+ Database: databasename "hris"

		+ Host: serveraddress "localhost"

		+ Post: defaultpostgresport "5432"

    * Save Global secret key:
	- 4a4c7ff139bd79e577eebc95ead5310b7


**Developers Section**

    * Help on console commands
	app/console help

	app/console list   #List all commands offered by console

	app/console --list #List all commands offered by console

    * Create a bundle
	app/console generate:bundle

    * Management of assets on deployment
	Updating symbolic links to bundle assets
             php app/console assets:install --symlink web #Creates symbolic links to package assets

	Using assetic to generate static urls
             php app/console assetic:dump --env=prod --no-debug  #To generate assets static urls

    * Clearing web server cache
	php app/console cache:clear --env=prod --no-debug

	php app/console cache:clear --env=dev --no-warmup

    * Updating project package dependecies with composer.phar
	- Update composer itself:
		php composer.phar self-update

	- Update dependencies:
		php composer.phar update

	- Updating single repository:
		php composer.phar update friendsofsymfony/user-bundle

    * Generating doctrine entity
	php app/console doctrine:generate:entity

    * Checking existing routes in the project
	php app/console router:debug

    * Listing schema updates/changes
	php app/console doctrine:schema:update --dump-sql

    * Applying schema updates/changes
	php app/console doctrine:schema:update --force

    * Creating user account using fos user bundle commands
	php app/console fos:user:create

    * Promote user's roles using fos user bundle commands
	- php app/console for\:user\:promote	#Roles must start with ``ROLE_`` prefix

	- Documentation on FixturesBundle
		http://symfony.com/doc/current/bundles/DoctrineFixturesBundle/index.html

	- Documentation on Database Migrations
		http://symfony.com/doc/current/bundles/DoctrineMigrationsBundle/index.html

	- Documentation on Framework Extra Bundle
		https://github.com/sensio/SensioFrameworkExtraBundle/tree/master/Resources/doc

	- Documentation on JMS Security Extra bundle
		http://jmsyst.com/bundles/JMSSecurityExtraBundle/1.2

**Sonata Dependencies**

    * Exporter
	https://github.com/sonata-project/exporter

    * Knp Menu Bundle
	https://github.com/KnpLabs/KnpMenuBundle

    * Sonata Cache Bundle
	https://github.com/sonata-project/SonataCacheBundle

    * Sonata Block Bundle
	https://github.com/sonata-project/SonataBlockBundle

    * Sonata JQuery Bundle
	https://github.com/sonata-project/SonatajQueryBundle