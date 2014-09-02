---
layout: post
title: "A Cookiecutter template for Flask-based Web Applications"
published: true
---

Recently, I started a github project 
[ryanolson/cookiecutter-webapp](https://github.com/ryanolson/cookiecutter-webapp)
as a means to jumpstart the process of starting a new web application.  While there
remains a lot todo (and to document), it seems like a good time to open it up and 
hopefully get some useful feedback.

## Features

The following is a list of core technologies used:

- [Vagrant](http://vagrantup.com) to bring up a local development server
- [Ansible](http://ansible.com) for provisioning
- [Flask](https://github.com/mitsuhiko/flask) WSGI application
- [Nginx](http://nginx.com) configured reverse-proxy with [h5bp/server-configs-nginx](https://github.com/h5bp/server-configs-nginx) best practices
- [PostgreSQL](http://www.postgresql.org) running on the provisioned VM
- [Grunt](http://gruntjs.com) and [Bower](http://bower.io) to manage web assets
- [Pragmatic Stateless RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
  using a combination of [Flask-Classy](https://github.com/apiguy/flask-classy) and
  [Flask-RESTful](https://github.com/twilio/flask-restful).
- Dynamic user interface based on [React](http://facebook.github.io/react/) and
  [Backbone.JS](http://backbonejs.org)
- [Flask-SQLAlchemy](https://github.com/mitsuhiko/flask-sqlalchemy) with basic User model
- Secure logins via [Flask-Security](https://github.com/mattupstate/flask-security),
  [Flask-WTForms](https://github.com/lepture/flask-wtf)
- Revocable JSON Web Tokens (JWT) for API authentication via [Flask-JWT](https://github.com/mattupstate/flask-jwt)
- Easy database migrations with [Flask-Migrate](https://github.com/miguelgrinberg/Flask-Migrate)
- [Twitter's Bootstrap 3](http://getbootstrap.com) and
  [Font Awesome 4](http://fortawesome.github.io/Font-Awesome/)
- [pytest](http://pytest.org/latest/),
  [WebTest](http://webtest.readthedocs.org/en/latest/), and
  [Factory-Boy](http://factoryboy.readthedocs.org/en/latest/) for testing
- A simple [Flask-Script](https://github.com/smurfix/flask-script) `manage.py` script.
- Useful [debug toolbar](https://github.com/mgood/flask-debugtoolbar)

## Getting Started

### Step 1: Customize Your Project

The [base project](https://github.com/ryanolson/cookiecutter-webapp) is a
[cookiecutter](https://github.com/audreyr/cookiecutter) template.  Therefore,
Step 1 is to create your customized project from the template using cookiecutter.

{% gist 7eb35dd67646dfe40afc install-cookiecutter %}

You will be asked some basic info about the project you wish to create:

- `app_name`: snake case name of the application
- `AppName`: CamelCase name of the application
- `project_name`: name of your applications, human form
- `license`
    * `MIT`
    * `GPLv3`
    * `GPLv2`
    * `Apache`
    * `ISC`
    * `Mozilla`
    * any other license - you will have to add the text to the LICENSE file
- `author`
- `email`
- `company`
- `copyright`: usually takes the form of "Year, Company/Author" (@ will be prepended)
- `app_repo`: git repository for storing your code
- `app_url`: the url for the hosted project
- `vagrant_ipv4`: the host-only IP address for the vagrant-managed virtual
   machine that will be created and provisioned. 

That's it!  Cookiecutter will have generated your customized webapp project folder.

### Step 2: Fire it up

In this step, you will be creating and provisioning a virtual machine to
run your web app. You will need [Vagrant](http://vagrantup.com),
[Ansible](http://ansible.com), and
[VirtualBox](https://www.virtualbox.org/wiki/Downloads) installed on your machine.

To launch your VM, simply type `vagrant up` from the top-level directory of your
created project.

After Vagrant and Ansible do their work, direct your browser to
<https://192.168.100.10> or whatever IP address you specifed for `vagrant_ipv4`.

### Step 3: Develop your web app

Read the README.md file created in your project directory for more details on development, testing and deployment.

## More Info

Over the next few weeks, I'll add articles discussing:

- Vagrant / Ansible provisioning
- A Pragmatic RESTful API using Flask-Classy, Flask-RESTful and Flask-Restless
- Backbone.js + Conditional API - handling 304s
- Backbone.js + JWT - handling expired tokens and reissuing requests
- Flask-JWT + Revokeable tokens