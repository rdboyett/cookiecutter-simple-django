cookiecutter-simple-django-bootstrap
==========================

A cookiecutter_ template for Django.

.. _cookiecutter: https://github.com/audreyr/cookiecutter

Description
-----------

Lighter version of the Daniel Greenfeld's cookiecutter-django with bootstrap added.

It uses the latest stable versions and it only defines a skeleton which can be extended as needed.

Usage
------

Let's pretend you want to create a Django project called "redditclone". Rather than using `startproject`
and then editing the results to include your name, email, and various configuration issues that always get forgotten until the worst possible moment, get cookiecutter_ to do all the work.

First, get cookiecutter. Trust me, it's awesome::

Set up your virtualenv::

    $ cd <your-envs-folder>
    $ virtualenv  --no-site-packages redditclone
    $ cd redditclone
    $ source bin/activate
    $ pip install cookiecutter

Now run it against this repo::

    $ cd <your-workspace>
    $ cookiecutter  https://github.com/marcofucci/cookiecutter-simple-django.git

You'll be prompted for some questions, answer them, then it will create a Django project for you.


**Warning**: After this point, change 'Marco Fucci', etc to your own information.

It prompts you for questions. Answer them::

    Cloning into 'cookiecutter-django'...
    remote: Counting objects: 443, done.
    remote: Compressing objects: 100% (242/242), done.
    remote: Total 443 (delta 196), reused 419 (delta 176)
    Receiving objects: 100% (443/443), 119.91 KiB | 0 bytes/s, done.
    Resolving deltas: 100% (196/196), done.
    project_name (default is "project_name")? redditclone
    repo_name (default is "repo_name")? redditclone
    author_name (default is "Your Name")? Marco Fucci
    email (default is "Your email")? <your-email>
    description (default is "A short description of the project.")? A reddit clone
    year (default is "Current year")? 2013
    with_documentation (default is "yes")? yes

If you are using cookiecutter < 0.7 and you answered *no* to *with_documentation*, you might want to delete the ``docs`` 
folder. 
From version 0.7+, that folder is automatically deleted for you.


Create the database ``redditclone`` and then set up your project::

    $ cd redditclone/
    $ ls
    $ pip install -r requirements/local.txt
    $ python ./manage.py makemigrations
    $ python ./manage.py migrate
    $ python ./manage.py runserver

and load localhost:8000/admin


Create a GitHub repo and push it there::

    $ git init
    $ git add .
    $ git commit -m "first awesome commit!"
    $ git remote add origin git@github.com:marcofucci/redditclone.git
    $ git push -u origin master

To add your own requirements, just activate your virtual environment, pip freeze it and
update your requirements files::

    $ activate <your-envs-folder>/redditclone/bin/activate
    $ pip freeze
    $ # now open requirements/* and note down the versions used.


Structure
---------

The structure used should look quite familiar:

**Requirements**

The ``requirements`` folder contains a requirements file for each environment.

If you need to add a dependency please choose the right file.

**Settings**

The ``settings`` folder contains a settings file for each environment and the ``local`` settings should be gitignored.

If you take a look at ``base.py``, you'll see that it includes the optional module ``local.py``
in the same folder. There you can override the local values and gitignore will
exclude it from your commits.

The ``testing.py`` module is loaded automatically after ``base.py`` and ``local.py`` every time you
run ``python ./manage.py test``.

**Apps**

When it's time to ``python ./manage.py startapp <name>``.

Done!
-----

Now, it's time to write the code!!!

