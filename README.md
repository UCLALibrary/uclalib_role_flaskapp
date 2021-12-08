uclalib_role_flaskapp
=========

An ansible role that installs a python Flask application on a RHEL 7 system.

**This role is no longer maintaned and the repo is archived**

Requirements
------------

For a RHEL system, it must already be subscribed to Red Hat and base repositories enabled via `uclalib_role_rhel7repos`

Role Variables
--------------

  * `app_name` - Defines the name of the Flask application - this typically matches the filename for the main python flask .py file.

  * `app_object` - Defines the name of the call-able Flask object in the main python flask .py file - for example if `MyApp = Flask(__name__)` is defined, then `MyApp` is the value for `app_object`.

  * `app_user` - Defines the name of the system user that will own the Flask application files.

  * `app_user_home_dir` - Defines the home directory of `app_user`.

  * `app_base_dir` - Defines the base filesystem path where the Flask application files will be deployed.

  * `app_python_version` - Defines the version of python to be used for this Flask application - takes the form of: `36`, `34`, `3`, `2`.

  * `python_libraries` - Defines a list of python libraries needed by this Flask application.

  * `app_host_fqdn` - Defines the fully qualified domain name of the server running this Flask application.

  * `git_repo_url` - Defines the URL to the Git repo hosted the Flask application code base.

  * `git_repo_branch` - Defines the git branch of the Flask application that should be deployed.

If this Flask application uses a database backend:

  * `app_db_host` - defines the hostname of the database.

  * `app_db_name` - defines the name of the database.

  * `app_db_user` - defines the username will privileges to connect to the database.

  * `app_db_pass` - defines the password for the user to connect to the database.

Dependencies
------------

  * `uclalib_role_rhel7repos`
  * `uclalib_role_epel`
  * `uclalib_role_uclalibrepo`
  * `uclalib_role_ruby`
  * `uclalib_role_apache`
  * `uclalib_role_passenger`
  * `uclalib_role_pip`

Example Playbook
----------------

```
---

- name: uclalib_flaskapp.yml
  become: yes
  become_method: sudo
  hosts: all
  user: ansible

  roles:
    - { role: uclalib_role_ruby }
    - { role: uclalib_role_apache }
    - { role: uclalib_role_passenger }
    - { role: uclalib_role_pip }
    - { role: uclalib_role_flaskapp }

```
