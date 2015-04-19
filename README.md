ansible-django-stack
====================

Ansible Playbook designed for environments running a Django app.  It can install and configure these applications that are commonly used in production Django deployments:
- MySQL
- Virtualenv

Default settings are stored in ```roles/role_name/vars/main.yml```.  Environment-specific settings are in the ```env_vars``` directory.

**Tested with OS:** Ubuntu 12.04.4 LTS x64

## Getting Started
A quick way to get started is with Vagrant and VirtualBox.

### Requirements
- [Ansible](http://docs.ansible.com/intro_installation.html)
- [Vagrant](http://www.vagrantup.com/downloads.html)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

The main settings to change here is in the **env_vars/base** file, where you can configure the location of your Git project, the project name, and application name which will be used throughout the Ansible configuration.

All you really have to do is type in this one command in the project root:
```
vagrant up
```

Wait a few minutes for the magic to happen.  

### Run Django server

One of the reason you need to run Django server is to inspect data with Django admin.
To do this you should type:

```
vagrant ssh
```

in vagrant session:

```
cd /webapps/housing_survey
source bin/activate
cd housing-survey
# create superuser with any login/pass you want
python manage.py createsuperuser
# run Django
python manage.py runserver 0.0.0.0:8080
```

Open your browser at http://192.168.33.15:8080/admin, enter login and password you've created before. Enjoy!
