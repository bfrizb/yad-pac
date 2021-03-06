[![Build Status](https://travis-ci.org/bfrizb/passgify.svg?branch=master)](https://travis-ci.org/bfrizb/passgify)

Passgify
====================================================

A tool to deterministically generate pseudo-random passwords.

Running Passgify
----------------

### Install Instructions ###

* Download repo
* `cd passgify`
* `sudo python setup.py install`
* Run: `pg -h`

### Run Example (Post-Install) ###

From the command line use `pg -h` to get the help menu for passgify

You might for example enter `pg yelp` to generate a password for your account on yelp.com.

### Configuration File and Secret Key ###

If it's your first time running passgify, you will be asked to choose values that will be used by passgify when generating your password (e.g. the default password prefix). For example:
`Choose default Password LENGTH [32]:`
These values will be saved to a configuration file. You can leave the answers blank to accept the default values shown in brackets (e.g. a default length of 32).
Consider saving a backup copy of your configuration files, since if you lose your configuration file or secret key (discussed below), you will have no way to correctly regenerate passwords created by passgify.

Every time you run passgify, you will be asked to enter your Secret Key (i.e. "Master Password") in order to generate passwords.
If you enter the wrong Secret Key, passgify will not generate any error message. It will simply generate an incorrect password.

FAQs
----------------

* How do you pronounce "passgify"?
  * Passgify is pronounced like "pacify", but with a 'g' instead of a 'c' sound

Dev Instructions
----------------

* Download repo
* `cd passgify`
* (On OSX) `sudo easy_install pip && sudo pip install -r requirements.txt`
* `make test`

### Dev Tools used in this Project ###

* [git](https://git-scm.com/) for source/version control
  * Update `.gitignore` with files that shoud not be tracked
* [Makefile](http://mrbook.org/blog/tutorials/make/) for running commands
  * `make test` runs tests against the source code
  * `make clean` removes extra files under the root of this project that are generated by tools
* [pre-commit](http://pre-commit.com/) for code style enforcement
  * `.pre-commit_config.yaml` specifies the code style rules that will be enforced as githooks
  * Running pre-commit will often automatically fix code style errors
  * `make test` first runs pre-commit against all files tracked by git
* [tox](https://tox.readthedocs.org/en/latest/) for running code tests in virtual environments (virtualenv's)
  * tox.ini instructs tox to run tests placed in the `tests` directory using python2.7
  * `make test` runs tox after running pre-commit
* [coverage](https://coverage.readthedocs.org/en/coverage-4.0.3/) for measuring code coverage of Python tests
  * tox invokes coverage (as specified in tox.ini)
