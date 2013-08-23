.. installation:

.. index:: Installing HRIS Software

Installing HRIS Software
=======================

**PHP5-INTL Dependency**

    On Systems running Linux Operating systems run::

      sudo apt-get install php5-intl

    On Systems running Mac OSX Operating systems run::

      brew install icu4c

    **Download system source codes from our** `github repository <https://github.com/hrisproject/hris>`_ - https://github.com/hrisproject/hris::

        git clone git@github.com:hrisproject/hris.git
        
    Install composer inside project directory - hris Note: hris now comes with composer pre-installed::

        curl -s https://getcomposer.org/installer | php

    .. note:: 

       If you don't have curl, install composer with this script php -r "eval('?>'.file_get_contents('https://getcomposer.org/installer'));"

    Update your repository with latest dependecies::

        php composer.phar install

        php composer.phar update

    Symbolic Link your web directory to the webroot directory::

        ln -s ${PWD}/web/ /var/www/hris     #Assuming your current directory(PWD) is inside hris project and your webroot is on /var/www/

    Set date time zone inside php.ini to your location,change line date.timezone to your locale, e.g in `Dar-es-salaam, Tanzania`::

        date.timezone = 'Africa/Dar_es_Salaam'

    Turn off short_open_tag inside php.ini to disable detection of PHP codes between <? and ?> for better PHP >=5.3 Experience::

        short_open_tag = Off

    Give Web readwrite access to cache and log directory in your hris directory. To enjoy both user and web read-write access in linux use the following commands::

        rm -rf app/cache/*

        rm -rf app/logs/*

    On Systems supporting chmod +a(e.g. Mac), you can give readwrite permission via::

        sudo chmod +a "www-data allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs

        sudo chmod +a "`whoami` allow delete,write,append,file_inherit,directory_inherit" app/cache app/logs

    On Systems that don't support chmod +a(e.g. Linux), you can give readwrite permission via::

        sudo setfacl -R -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs

        sudo setfacl -dR -m u:www-data:rwx -m u:`whoami`:rwx app/cache app/logs

.. index:: Database Setup

Database Setup
==============

`System source code can be downloaded from github <https://github.com/hrisproject/hris>`_

    Configuration file can be found from hris/app/config/parameters.yml

**Parameters.yml**::

        database_driver: pdo_pgsql
        database_host: %databasehost%
        database_port: %portnumber%
        database_name: %databasename%
        database_user: %databaseuser%
        database_password: %userpassowrd%
        mailer_transport: smtp
        mailer_host: %mailerhost%
        mailer_user: null
        mailer_password: null
        locale: en
        secret: %secret_generated_key%
        database_path: null

**Generating database**::

        app/console doctrine:database:drop --force      #Drops Database if it exist
        app/console doctrine:database:create            #Creates Fresh new database
        app/console doctrine:schema:update --force      #Updates Database schema
        app/console list                                #List all commands offered

**Creating, Activating,Changing password, deactivate, demote & promote login-user from commandline**::

        app/console fos:user:create                     #Create User account
        app/console fos:user:activate                   #Activate a user
        app/console fos:user:change-password            #Change the password of a user.
        app/console fos:user:create                     #Create a user.
        app/console fos:user:deactivate                 #Deactivate a user
        app/console fos:user:demote                     #Demote a user by removing a role
        app/console fos:user:promote                    #Promotes a user by adding a role

**Regenerating assets**::

        app/console assetic:dump
        php app/console assets:install web

**Shell Console**::

        app/console --shell

.. index:: Performance tuning

Performance tuning
==================

::

        File php.ini can be used to tweak performance of the system 