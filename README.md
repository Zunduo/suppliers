## DevOps - Supplier

[![Build Status](https://travis-ci.com/nyusuppliers/suppliers.svg?branch=main)](https://travis-ci.com/nyusuppliers/suppliers)
[![codecov](https://codecov.io/gh/nyusuppliers/suppliers/branch/main/graph/badge.svg?token=VWAL4SIAK2)](https://codecov.io/gh/nyusuppliers/suppliers)

## Introduction

This project is the back end for an eCommerce web site as a RESTful microservice for the Suppliers. An Supplier is a vendor from whom we get products from. This microservice supports the complete Create, Read, Update, & Delete (CRUD) lifecycle.


## How to access

#### Running on IBM Cloud in Dev:

https://nyu-supplier-service-sum21-dev.us-south.cf.appdomain.cloud

#### Running on IBM Cloud in Prod:

https://nyu-supplier-service-sum21.us-south.cf.appdomain.cloud

#### DevOps Pipeline:

https://cloud.ibm.com/devops/pipelines/4bf3eb13-4e76-4496-affe-fa81bd552499?env_id=ibm:yp:us-south

#### DevOps API Docs:
https://nyu-supplier-service-sum21.us-south.cf.appdomain.cloud/apidocs

## Repository Structure
```
service
├─ __init__.py     - package initializer
├─ models.py       - service database models
├─ routes.py       - service routes settings
└─ status.py       - service status codes

tests
├─ __init__.py     - test initializer
├─ factories.py    - module to generate the fake data
├─ test_models.py  - test case for the models service
└─ test_routes.py  - test case for the routes service
```

## Database Deisgn Attributes

| Field | Type | Primary Key | Descriptions 
| :--- | :--- | :--- | :--- |
| id | Integer | True | ID of the supplier 
| name | String | False | Name of the individual or company name 
| phone | String | False | Phone number of the supplier 
| address | String | False| Address of the supplier
| available | Boolean(default True) |False | supplier availbility
| product_list | Integer List | False | Product id lists for each supplier
| rating | Float | False | Supplier rating 

## Run the test service on Your Local PC

### Prerequisite Installations
Download [VirtualBox](https://www.virtualbox.org/) and [Vagrant](https://www.vagrantup.com/).

For unix user, we recommend to install the environment via Homebrew:
```
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Then Executing the command to finish the installation:
```
$ brew install git
$ brew install --cask virtualbox
$ brew install --cask vagrant
```

### Executing the TDD Unit Test
To executing the service, type the following command in the terminal SSH:
```
$ git clone https://github.com/nyusuppliers/suppliers.git
$ cd suppliers
$ vagrant up
$ vagrant ssh
$ cd /vagrant
$ nosetests
```
To see the coverage report, type:
```
$ coverage report -m
```

### Close Service
Once finish, to close the VM and terminate service. Please type:
```
$ exit
$ vagrant halt
```
Once finish testing and no longer need it again. Please type following command to delete the service.
```
$ vagrant destroy
```
## API Reference 

### LIST 
- End Point: **GET** /suppliers?param={query_param}
- Query Parameters:
    - name (string)
    - phone (string)
    - address (string)
    - available (boolean)
    - rating (string)
    - product_id (string)

### READ 
- End Point: **GET** /suppliers/{supplier_id}
- Path Parameters:
    - supplier_id (int)

### CREATE 
- End Point: **POST** /suppliers 
- Body Parameters:
    - name (string)
    - phone (string)
    - address (string)
    - available (boolean)
    - rating (float)
    - product_id (list of int)

### UPDATE
- End Point: **PUT** /suppliers/{supplier_id}
- Path Parameters:
    - supplier_id (int)
- Body Parameters:
    - name (string)
    - phone (string)
    - address (string)
    - available (boolean)
    - rating (float)
    - product_id (list of int)    

### DELETE
- End Point: **DELETE** /suppliers/{supplier_id}
- Path Parameters:
    - supplier_id (int)

### PENALIZE
- End Point: **PUT** /suppliers/{supplier_id}/penalize
- Path Parameters:
    - supplier_id (int)
    
