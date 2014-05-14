Python Web Development with Flask
=================================

This repository contains the source code that I demonstrated in my O'Reilly webcast [Python Web Development with Flask](http://www.oreilly.com/pub/e/3040).

Requirements
------------

To install and run this application you need:

- Python 2.7 or 3.3+
- virtualenv (not required if you are using Python 3.4)
- git (only to clone this repository)

Installation
------------

The commands below install the application and its dependencies:

    $ git clone https://github.com/miguelgrinberg/flask-webcast.git
    $ cd flask-webcast
    $ virtualenv venv
    $ . venv/bin/activate
    (venv) pip install -r requirements.txt

Note for Python 3.4 users: replace `virtualenv` with `pyvenv`.

Note for Microsoft Windows users: replace the virtual environment activation command above with `venv\Scripts\activate`.

Running
-------

This project is composed of five different applications located in sub-directories named as follows:

- 01-hello-world
- 02-templates
- 03-forms
- 04-database
- 05-structure

To run applications one through four you have to cd into the directory and run the `hello.py` script in it. For example:

    (venv) $ cd 01-hello-world
    (venv) $ python hello.py

For the fourth application you need to set up a Mongo database before you can use the application. The connection URL to this database must be stored in a `MONGO_URI` environment variable. For the live demonstration in the webcast a free cloud based database from http://mongohq.com was used, this is a good alternative if you don't want to go through the effort of installing the database server on your computer.

The fifth application is started by running a script called `manage.py`. Before you run the application you need to select which configuration to run, which can be `development` or `production`. Depending on the selected configuration a second environment variable configures the Mongo database. To run the server in development mode you can run the following commands in a bash shell:

    (venv) $ cd 05-structure
    (venv) $ FLASK_CONFIG=development MONGO_DEV_URI=http://<your-mongodb-url-here> python manage.py runserver

If you are doing this on Windows then the commands are as follows:

    (venv) $ cd 05-structure
    (venv) $ set FLASK_CONFIG=development
    (venv) $ set MONGO_DEV_URI=http://<your-mongodb-uri-here>
    (venv) $ python manage.py runserver

Note that when running the application in production mode the Mongo URL is specified in the `MONGO_URI` environment variable. Different variables are used for each mode to allow all modes to be configured in the same computer.

Once the server starts you can open `http://localhost:5000` in your web browser to see the application in action. To stop the application use Ctrl+C.

See the [webcast](http://www.oreilly.com/pub/e/3040) for a live demonstration.

Unit tests
----------

The fifth version of the application can also run unit tests. The command to run them is as follows:

    (venv) $ MONGO_TEST_URI=http://<your-mongodb-test-uri_here> python manage.py test
    test_app_exists (test_basics.BasicsTestCase) ... ok
    test_app_is_testing (test_basics.BasicsTestCase) ... ok
    test_names (test_basics.BasicsTestCase) ... ok
    
    Name               Stmts   Miss Branch BrMiss  Cover   Missing
    --------------------------------------------------------------
    app                   10      0      0      0   100%
    app.hello              3      0      0      0   100%
    app.hello.routes      12      0      4      0   100%
    --------------------------------------------------------------
    TOTAL                 25      0      4      0   100%
    ----------------------------------------------------------------------
    Ran 3 tests in 9.338s
    
    OK

If you are using Windows then the equivalent commands are:

    (venv) $ set MONGO_TEST_URI=http://<your-mongodb-test-uri-here>
    (venv) $ python manage.py test

It is recommended that you use a different database for testing. 

After the tests run you can see a coverage report. This gives you an idea of how much of the application code the tests touch.

