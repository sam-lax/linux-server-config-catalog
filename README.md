# Linux Server Configuration Project
### by Sam Lax

----

## Connecting to Lightsail Instance

* Locate SSH key content via "Notes to Reviewer" submission;
* Create a file with the appropriate permissons in your ~/.ssh directory and insert the SSH key content into it;
* Finally, run:

        ssh grader@184.73.21.80 -p 2200 -i ~/.ssh/{SSHKeyFile}

* You are now connected to my Lightsail instance!


---


## Software Summary
### Installation
* Installed via **apt-get**:

> finger, apache2, libapache2-mod-wsgi, postgresql, python-pip, python-sqlalchemy, python-psycopg2, python-itsdangerous, python-passlib, python-oauth2client python-requests, python-redis

* Installed via **pip**:

> Flask-HTTPAuth

### Configuration
* Apache2:
  * Created new .conf file in /etc/apache2/sites-available/;
  * Replaced 000-default.conf with new .conf file;
  * Enabled new site;
  * Restarted service.
* PostgreSQL:
  * Created users/roles with privileges needed to deliver and build the application, including "pyuser" and "www-data";
  * Granted SELECT, INSERT, DELETE and UPDATE on catalog's items and categories tables to users listed above;
  * Granted the above privileges to pyuser for catalog database's users table.
* UFW:
  * Denied TCP port 22 and all other not white-listed port/protocol connections (incoming/outgoing);
  * Allowed outgoing TCP port 80 and 123;
  * Allowed incoming TCP port 2200 via SSH.


---


## Resources
* Turtorials:
  * http://lucumr.pocoo.org/2007/5/21/getting-started-with-wsgi/
  * http://wsgi.tutorial.codepoint.net/intro
  * https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
* Documentation:
  * http://flask.pocoo.org/docs/1.0/deploying/mod_wsgi/
* Video:
  * https://www.youtube.com/watch?v=wq0saslschw
