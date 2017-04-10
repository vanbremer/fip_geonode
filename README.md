# fip_geonode Project

FIP GeoNode project generated from GeoNode template project (https://github.com/GeoNode/geonode-project) using a Virtualenvironment.

### Created the custom project using a Virtualenvironment

To setup the project using a local Virtualenvironment, these instructions were followed:

1. Setup your virtualenvironment ``mkvirtualenv fip_geonode``
2. Install django into your virtualenviornment ``pip install Django==1.8.7``
3. Create your project using the template project::
```
    django-admin.py startproject --template=https://github.com/GeoNode/geonode-project/archive/2.6.zip -epy,rst,yml fip_geonode
```


### Key project files

#### manage.py

``manage.py`` is the main entry point for managing the project during development. It allows running all the management commands from each app in the project. When run with no arguments, it will list all of the management commands.

#### settings.py

``settings.py`` is the primary settings file for the project. It is quite common to put all sensible defaults here and keep deployment specific configuration in the local_settings.py file. All of the possible settings values and their meanings are detailed in the Django documentation.


#### urls.py

``urls.py`` is where the application specific URL routes go. Additionally, any overrides can be placed here, too.

#### wsgi.py

This is a generated file to make deploying the project to a WSGI server easier. Unless there is very specific configuration needed, wsgi.py can be left alone.

#### setup.py

There are several packaging options in python but a common approach is to place the project metadata (version, author, etc.) and dependencies in ``setup.py``.


#### static

The ``static`` directory will contain the fixed resources: css, html, images, etc. Everything in this directory will be copied to the final media directory (along with the static resources from other apps in the project).


#### templates

All of the project's templates go in the ``templates`` directory. While no organization is required for the project specific templates, when overriding or replacing a template from another app, the path must be the same as the template to be replaced.

### Usage


Rename the local_settings.py.sample to local_settings.py and edit it's content by setting the SITEURL and SITENAME.

Edit the file /etc/apache2/sites-available/geonode and change the following directive from:

    WSGIScriptAlias / /var/www/geonode/wsgi/geonode.wsgi

to:

    WSGIScriptAlias / /path/to/my_geonode/my_geonode/wsgi.py
    
To avoid having to grant apache permissions (i.e. www-data user and group) to your home dir where you likely setup the geonode-project; you may want to instead copy the wsgi.py file next to geonode.wsgi and replace the file name instead of the entire path.

    $ cp /path/to/my_geonode/my_geonode/wsgi.py /var/www/geonode/wsgi/wsgi.py

Add the "Directory" directive for your folder like the following example:

    <Directory "/home/vagrant/my_geonode/my_geonode/">

       Order allow,deny

       Options Indexes FollowSymLinks

       Allow from all

       Require all granted

       IndexOptions FancyIndexing
       
    </Directory>

Restart apache::

    $ sudo service apache2 restart

Edit the templates in my_geonode/templates, the css and images to match your needs.

In the my_geonode folder run::

    $ python manage.py collectstatic

### Github Considerations

While it is helpful to recommit your django project wrapper back to a distributed version control repository. 
* It is also important to remember that production instances will store security information in the local_settings.py
* Admin/Devs should always remember to exclude this file in the .gitignore file in the same folder as the .git::

    $ nano .gitignore
    
    /{project}/local_settings.py

save, make sure the file is also removed from git cache::
    
    $ git rm -f --cache //local_settings.py
    
    $ git status
    
confirm the file is no longer staged for the next commit or that if it is as "removed"
