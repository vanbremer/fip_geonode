# fip_geonode Project

FIP GeoNode project generated from GeoNode template project (https://github.com/GeoNode/geonode-project) using a Virtualenvironment.

## Created the custom project using a Virtualenvironment

To setup the project using a local Virtualenvironment, these instructions were followed:

1. Setup your virtualenvironment ``mkvirtualenv fip_geonode``
2. Install django into your virtualenviornment ``pip install Django==1.8.7``
3. Create your project using the template project::

    django-admin.py startproject --template=https://github.com/GeoNode/geonode-project/archive/master.zip -epy,rst,yml fip_geonode


## Key project files

### manage.py

``manage.py`` is the main entry point for managing the project during development. It allows running all the management commands from each app in the project. When run with no arguments, it will list all of the management commands.

### settings.py

``settings.py`` is the primary settings file for the project. It is quite common to put all sensible defaults here and keep deployment specific configuration in the local_settings.py file. All of the possible settings values and their meanings are detailed in the Django documentation.


### urls.py

``urls.py`` is where the application specific URL routes go. Additionally, any overrides can be placed here, too.


### wsgi.py

This is a generated file to make deploying the project to a WSGI server easier. Unless there is very specific configuration needed, wsgi.py can be left alone.

### setup.py

There are several packaging options in python but a common approach is to place the project metadata (version, author, etc.) and dependencies in ``setup.py``.


### static

The ``static`` directory will contain the fixed resources: css, html, images, etc. Everything in this directory will be copied to the final media directory (along with the static resources from other apps in the project).


### templates

All of the project's templates go in the ``templates`` directory. While no organization is required for the project specific templates, when overriding or replacing a template from another app, the path must be the same as the template to be replaced.
