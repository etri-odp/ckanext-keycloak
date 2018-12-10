.. You should enable this project on travis-ci.org and coveralls.io to make
   these badges work. The necessary Travis and Coverage config files have been
   generated for you.

.. .. image:: https://travis-ci.org/etri-sodas/ckanext-keycloak.svg?branch=master
    :target: https://travis-ci.org/etri-sodas/ckanext-keycloak

.. .. image:: https://coveralls.io/repos/etri-sodas/ckanext-keycloak/badge.svg
  :target: https://coveralls.io/r/etri-sodas/ckanext-keycloak

.. .. image:: https://pypip.in/download/ckanext-keycloak/badge.svg
    :target: https://pypi.python.org/pypi/etri-sodas/ckanext-keycloak/
    :alt: Downloads

.. .. image:: https://pypip.in/version/ckanext-keycloak/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-keycloak/
    :alt: Latest Version

.. .. image:: https://pypip.in/py_versions/ckanext-keycloak/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-keycloak/
    :alt: Supported Python versions

.. .. image:: https://pypip.in/status/ckanext-keycloak/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-keycloak/
    :alt: Development Status

.. .. image:: https://pypip.in/license/ckanext-keycloak/badge.svg
    :target: https://pypi.python.org/pypi/ckanext-keycloak/
    :alt: License

===========================================================
ckanext-keycloak - Keycloak authentication extension
===========================================================

.. Put a description of your extension here:
   What does it do? What features does it have?
   Consider including some screenshots or embedding a video!

ckanext-keycloak is an extension for enabling user authentication with Keycloak, an open source software product to allow single sign-on (SSO) with Identity Management and Access Management aimed at modern applications and services.

This extension provides the ability for users to use access-tokens from Keycloak server to access CKAN functions via CKAN REST API.

Notes:

* A new user will be created automatically in ckan database for the corresponding keycloak user if it does not exist.
* Original ckan authentication still works normally with this extension.

------------
Requirements
------------

This extension was developed and tested under CKAN-2.7.3 and Keycloak-2.5.5

------------
Installation
------------

.. Add any additional install steps to the list below.
   For example installing any non-Python dependencies or adding any required
   config settings.

To install ckanext-keycloak:

1. Activate your CKAN virtual environment, for example::

    . /usr/lib/ckan/default/bin/activate

2. Install the ckanext-keycloak Python package into your virtual environment::

    pip install ckanext-keycloak

3. Add ``keycloak`` setting in your CKAN config file (by default the config file is located at ``/etc/ckan/default/production.ini``) as follows::
   
    ckan.plugins = keycloak <other-plugins>
    ckan.keycloak.authorization_endpoint = http://localhost/auth
    ckan.keycloak.realm = master
    ckan.keycloak.client_id = client_id
    ckan.keycloak.client_secret = client_secret
    ckan.keycloak.sysadmin_group_name = admin
    ckan.keycloak.profile_group_field = group
    ckan.keycloak.profile_username_field = preferred_username
    ckan.keycloak.profile_email_field = email
    ckan.keycloak.profile_fullname_field = name
   
4. Restart CKAN. For example if you've deployed CKAN with Apache on Ubuntu::

    sudo service apache2 reload


------------------------
Development Installation
------------------------

To install ckanext-keycloak for development, activate your CKAN virtualenv and
do::

    git clone https://github.com/etri-odp/ckanext-keycloak.git
    cd ckanext-keycloak
    python setup.py develop
    pip install -r dev-requirements.txt


-----------------
Running the Tests
-----------------

To run the tests, do::

    nosetests --nologcapture --with-pylons=test.ini

To run the tests and produce a coverage report, first make sure you have
coverage installed in your virtualenv (``pip install coverage``) then run::

    nosetests --nologcapture --with-pylons=test.ini --with-coverage --cover-package=ckanext.keycloak --cover-inclusive --cover-erase --cover-tests


----------------------------------------------
Registering ckanext-keycloak on PyPI
----------------------------------------------

ckanext-keycloak should be availabe on PyPI as
https://pypi.python.org/pypi/ckanext-keycloak. If that link doesn't work, then
you can register the project on PyPI for the first time by following these
steps:

1. Create a source distribution of the project::

     python setup.py sdist

2. Register the project::

     python setup.py register

3. Upload the source distribution to PyPI::

     python setup.py sdist upload

4. Tag the first release of the project on GitHub with the version number from
   the ``setup.py`` file. For example if the version number in ``setup.py`` is
   0.0.1 then do::

       git tag 0.0.1
       git push --tags

================
Acknowledgements
================

This work was supported by Institute for Information & communications Technology Promotion (IITP) grant funded by the Korea government (MSIT) (No.2017-00253, Development of an Advanced Open Data Distribution Platform based on International Standards) 
