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

See the [webcast](http://www.oreilly.com/pub/e/3040) for a live demonstration.
