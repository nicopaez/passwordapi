# Scalability Workshop: Password API

[![Build Status](https://travis-ci.org/auth0-eng-camp/passwordapi.svg?branch=master)](https://travis-ci.org/auth0-eng-camp/passwordapi)

Password API provides the following features:

* Verifies if a password is strong enough (GET /valid)
* Given a password it returns its hash (GET /hash)
* Given a password and a hash it checks if they match (GET /check-match)
* Generates a random password (GET /password)


This API is built on NodeJS 8:

* To install dependencies: _npm install_
* To run tests: _npm test_
* To run the application: _npm start_
