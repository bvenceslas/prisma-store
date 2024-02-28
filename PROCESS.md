## DEVELOPMENT PROCESS

### Project Creation

1 - First We created the project with nest using `nest new prisma-store`, then selected `pnpm` as package manager.

2 - We installed the dependency **prisma** which is going to allow me initializing the prisma schema using `pnpm i prisma --save-dev`

3 - We initialized the prisma schema using `pnpm prisma init`

4 - We created the `docker-compose.yaml` file and set my mysql db image, then run `docker-compose up -d` to run the db using docker

### Running the migrations

There are three ways to run the prisma migrations

1. `pnpm prisma migrate dev --name init` this sets up a file locally where i can preview the changes done
2. `pnpm prisma migrate push --name init` this will automatically execute the migration without generating a local document
3. `pnpm prisma migrate deploy --name init` this allows you to apply the changes of your local database and deploy them to your production database

The property name helps to identify the migrations

### Database Initialization

To initialize database to connect to prisma, we use this following code in the database.service.ts file with:

```
import { Injectable, OnModuleInit } from '@nestjs/common';
import { PrismaClient } from '@prisma/client';

@Injectable()
export class DatabaseService extends PrismaClient implements OnModuleInit {
  async onModuleInit() {
    await this.$connect();
  }
}

```

### Bootstrapping product resource

To generate a product boilerplate for product we type `nest g resource products` specifying the type of the boilerplate to generate which is `REST`

After this, everything is ready to do a **CRUD Operations**
