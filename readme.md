# Prisma Basics and Demo

## Init

start services:
`docker compose up -d`

Set env vars to work with the db defined in docker-compose:

.env

```bash
DATABASE_URL="postgresql://myuser:mypassword@localhost:5432/mydb?schema=public"
```

## Prisma stuff

### creating your first migration (initial migration)

After defining a `generator`, `datasource` and at least one `model`, you can go ahead and create a migration to initialize the database (make sure your connection string is defined in your .env)

Create a migration and name it "init"
`npx prisma migrate dev --name init`

### Prisma Client

The prisma client allows you to issue queries in a class-method structure (enables autcomplete and other conveniences). To use this, you need to import the `@prisma/client` package

`npm install @prisma/client`

and import `PrismaClient` to be able to make the convenient quereis using objects that relate directly to your custom scheam

`import { PrismaClient } from "@prisma/client";`

**NOTE** Every time you make a change to your schema and want your autocomplete to reflect this, you will need to rerun `prisma generate`. The prima client saves the generated code in node_modules/.prisma/client. This means that if changes were done to the schema, or if you clean the node_modules folder, you will need to rerun prisma generate. Automate this.

`npx prisma generate`
