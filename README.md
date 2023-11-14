Getting started
Installation
Clone the repository

git clone https://github.com/lujakob/nestjs-realworld-example-app.git
Switch to the repo folder

cd nestjs-realworld-example-app
Install dependencies

npm install
Copy config file and set JsonWebToken secret key

cp src/config.ts.example src/config.ts
Database
The codebase contains examples of two different database abstractions, namely TypeORM and Prisma.

The branch master implements TypeORM with a mySQL database.

The branch prisma implements Prisma with a mySQL database.

TypeORM
Create a new mysql database with the name nestjsrealworld
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

Prisma
To run the example with Prisma checkout branch prisma, remove the node_modules and run npm install

Create a new mysql database with the name nestjsrealworld-prisma (or the name you specified in prisma/.env)

Copy prisma config example file for database settings

cp prisma/.env.example prisma/.env
Set mysql database settings in prisma/.env

DATABASE_URL="mysql://USER:PASSWORD@HOST:PORT/DATABASE"
To create all tables in the new database make the database migration from the prisma schema defined in prisma/schema.prisma

npx prisma migrate save --experimental
npx prisma migrate up --experimental
Now generate the prisma client from the migrated database with the following command

npx prisma generate
The database tables are now set up and the prisma client is generated. For more information see the docs:

https://www.prisma.io/docs/getting-started/setup-prisma/add-to-existing-project-typescript-mysql
NPM scripts
npm start - Start application
npm run start:watch - Start application in watch mode
npm run test - run Jest test runner
npm run start:prod - Build application
