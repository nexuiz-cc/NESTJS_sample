# Getting started

## Installation

Clone the repository

    git clone https://github.com/nexuiz-cc/NESTJS_sample.git

Switch to the repo folder

    cd NESTJS_sample

Install dependencies
    
    npm install

Copy config file and set JsonWebToken secret key

    cp src/config.ts.example src/config.ts

----------

## Database

The codebase contains examples of two different database abstractions, namely [TypeORM](http://typeorm.io/) .
The branch `master` implements TypeORM with a mySQL database.
----------

##### TypeORM

----------

Create a new mysql database with the name `nestjsrealworld`\
(or the name you specified in the ormconfig.json)

Copy TypeORM config example file for database settings

    cp ormconfig.json.example

Set mysql database settings in ormconfig.json

    {
      "type": "mysql",
      "host": "localhost",
      "port": 3306,
      "username": "your-mysql-username",
      "password": "your-mysql-password",
      "database": "nestjsrealworld",
      "entities": ["src/**/**.entity{.ts,.js}"],
      "synchronize": true
    }

Start local mysql server and create new database 'nestjsrealworld'

On application start, tables for all entities will be created.

----------

## NPM scripts

- `npm start` - Start application
- `npm run start:watch` - Start application in watch mode
- `npm run test` - run Jest test runner 
- `npm run start:prod` - Build application