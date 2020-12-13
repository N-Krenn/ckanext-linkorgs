.. You should enable this project on travis-ci.org and coveralls.io to make
   these badges work. The necessary Travis and Coverage config files have been
   generated for you.

.. image:: https://travis-ci.org/N-Krenn/ckanext-linkorgs.svg?branch=master
    :target: https://travis-ci.org/N-Krenn/ckanext-linkorgs

.. image:: https://coveralls.io/repos/N-Krenn/ckanext-linkorgs/badge.svg
  :target: https://coveralls.io/r/N-Krenn/ckanext-linkorgs

.. image:: https://pypip.in/download/ckanext-linkorgs/badge.svg
    :target: https://pypi.python.org/pypi//ckanext-linkorgs/
    :alt: Downloads

.. image:: https://pypip.in/version/ckanext-linkorgs/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-linkorgs/
    :alt: Latest Version

.. image:: https://pypip.in/py_versions/ckanext-linkorgs/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-linkorgs/
    :alt: Supported Python versions

.. image:: https://pypip.in/status/ckanext-linkorgs/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-linkorgs/
    :alt: Development Status

.. image:: https://pypip.in/license/ckanext-linkorgs/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-linkorgs/
    :alt: License

=============
ckanext-linkorgs
=============

Simple CKAN extension to combine with https://github.com/N-Krenn/linkorgs-app



------------
Requirements
------------

Working CKAN Installation; only tested with version 2.8.4. Only changes that could influence the compatibility are in API-Link generation and content/template rendering of the datasets/packages. 


------------
Installation
------------

.. Add any additional install steps to the list below.
   For example installing any non-Python dependencies or adding any required
   config settings.

Note that you can apply configuration beforehand to avoid having to change it afterwards. See step 6 and Configuration beforehand to do so.

To install ckanext-linkorgs:

1. Activate your CKAN virtual environment, for example::

     . /usr/lib/ckan/default/bin/activate

2. Install the ckanext-linkorgs Python package into your virtual environment::

     pip install ckanext-linkorgs

3. Add ``linkorgs`` to the ``ckan.plugins`` setting in your CKAN
   config file (by default the config file is located at
   ``/etc/ckan/default/production.ini``).

4. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

     sudo service apache2 reload
     
5. Check if the plugin is working.

6. Optional: edit ckanext-linkorgs/ckanext/linkorgs/templates/package/read.html to fit your design needs. The standard only displays it standardly, without using additional CSS    to not interfere with the CKAN template. Either change it before installing the Extension, or follow the steps in Configuration.

NOTE: the standard Plugin creates an iframe that points to localhost:80/app.php, where the corresponding linkorgs-app should be present. (find app here: https://github.com/N-Krenn/linkorgs-app). You can either host it yourselves or wait for a public release of a centralized service. The Plugin will be updated with the centralized services URL as soon as available.


------------
Configuration
------------
This chapter presents the way on how to change the URL of the application and the style options, when the responding application is hosted and running. It follows the approaches on a docker-compose installation of ckan. For other installations please consult the CKAN documentation.

1. Access the docker container::

     docker exec -it ckan /bin/bash -c "export TERM=xterm; exec bash"

2. Access the virtual environment of your installation::

     source $CKAN_VENV/bin/activate && cd $CKAN_VENV/src/

3. Go to the direction the template file for the extension is located::

     cd ckanext-linkorgs/ckanext/linkorgs/templates/package
     
4. Edit the template file (JINJA2)::

     e.g. vi read.html
     
5. Edit the iframe-src tag (standard: src="http://Localhost:80/app.php? ...) to fit your location of the php webapp.

6. Optional: Apply design changes by for example editing the CSS style options.

7. Save the file and check an examplatory dataset. If the app is not being displayed, check for syntax errors or consult the CKAN log file. Restart CKAN after being finished.
