---
title: "How to Use Prisma with PostgreSQL in a Full-Stack App"
seoTitle: "Prisma & PostgreSQL: Integration Guide"
seoDescription: "Learn to set up Prisma with PostgreSQL in a full-stack app using Node.js, Express, and JavaScript for efficient database interactions"
datePublished: Fri Aug 15 2025 03:19:37 GMT+0000 (Coordinated Universal Time)
cuid: cmec9f3ko000902jx1e0g6hkn
slug: how-to-use-prisma-with-postgresql-in-a-full-stack-app
tags: postgresql, nodejs, full-stack, prisma

---

Modern full-stack applications often need a reliable and developer-friendly way to interact with databases. Prisma is an open-source ORM (Object Relational Mapper) that makes it easier to work with databases using a type-safe and auto-completed API.

In this tutorial, you'll learn how to set up Prisma with PostgreSQL in a full-stack JavaScript app using Node.js and Express. This guide will walk you through installing Prisma, connecting to your PostgreSQL database, creating a schema, running migrations and querying data.

### Prerequisites

Before you begin, make sure you have the following installed:

* Node.js (v16 or higher)
    
* PostgreSQL (locally or via a cloud provider like Supabase or Neon)
    
* npm or yarn
    

You should also be comfortable using the command line and writing basic JavaScript.

---

### Step 1 : Initialize a Node.js Project

First, create a new project folder and initialize a package.json file.

```bash
mkdir prisma-postgres-app
cd prisma-postgres-app
npm init -y
```

Then install the necessary dependencies:

```bash
npm install express
npm install prisma --save-dev
npm install @prisma/client
```

* `prisma` is the development toolkit.
    
* `@prisma/client` is the actual runtime client you’ll use in your code.
    

Now initialize Prisma:

```bash
npx prisma init
```

This creates a `prisma` folder with a `schema.prisma` file and a `.env` file.

---

### Step 2: Configure the PostgreSQL Connection

In your `.env` file, add your PostgreSQL connection string:

```bash
DATABASE_URL="<database_url>"
```

---

### Step 3: Define Your Data Model

Open the `schema.prisma` file and define your model. Here’s a simple `User` model:

```pgsql
generator client {
  provider = "prisma-client-js"
  output   = "../generated/prisma"
}

datasource db {
  provider = "postgresql"
  url      = env("DATABASE_URL")
}

model User {
  id        Int      @id @default(autoincrement())
  name      String
  email     String   @unique
  createdAt DateTime @default(now())
}
```

This schema defines a `User` table with an auto-incrementing `id`, a unique `email` and timestamps.

---

### Step 4: Run the Database Migration

To create the `User` table in your PostgreSQL database, run:

```bash
npx prisma migrate dev --name init
```

Prisma will generate a migration file and apply it to your database. It will also generate the Prisma Client for your project.

---

### Step 5: Set Up Express and Create Routes

Now let’s set up a simple Express server and use Prisma to interact with the database.

Create a `server.js` file:

```javascript
const express = require('express');
const { PrismaClient } = require('./generated/prisma/client.js');

const app = express();
const prisma = new PrismaClient();

app.use(express.json());

app.post('/users', async (req, res) => {
  const { name, email } = req.body;
  try {
    const user = await prisma.user.create({
      data: { name, email },
    });
    res.json(user);
  } catch (error) {
    res.status(500).json({ error: 'User creation failed' });
  }
});

app.get('/users', async (req, res) => {
  const users = await prisma.user.findMany();
  res.json(users);
});

app.listen(3000, () => {
  console.log('Server is running on http://localhost:3000');
});
```

This simple server:

* Creates a new user using the Prisma Client
    
* Retrieves all users from the database
    

View project structure:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752510686924/390e8ee4-d2e2-486f-b425-499f10ac4eba.png align="center")

---

### Step 6: Test the API

Start the server:

```bash
npx prisma generate
node server.js
```

Then, use a tool like [Postman](https://www.postman.com/) or `curl` to test the endpoints.

To create a user:

```bash
curl -X POST http://localhost:3000/users 
-H "Content-Type: application/json" 
-d '{"name": "Krish", "email": "krish@example.com"}'
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752510479786/9aef2a5d-218a-4ea6-a5c9-cfb5b1adf003.png align="center")

To get all users:

```bash
curl http://localhost:3000/users
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752510518848/df33ff6d-abb0-4c75-b4f4-4a7206b9e945.png align="center")

---

### Step 7: Query Filtering and More

You can now use Prisma's type-safe API to write advanced queries. Here’s an example of filtering users by email:

```javascript
const user = await prisma.user.findUnique({
  where: { email: 'krish@example.com' },
});
```

Or use conditions:

```javascript
const users = await prisma.user.findMany({
  where: {
    name: {
      contains: 'K',
    },
  },
});
```

---

### Final Thoughts

Prisma makes working with databases in full-stack apps much easier by providing a modern and intuitive ORM experience. With just a few commands, you can define your schema, generate client APIs and write safe, readable database queries.

From here, you can:

* Expand your data model
    
* Add error handling
    
* Integrate the backend with a front-end (like React or Next.js)
    

This setup is production-ready and scalable, especially when paired with tools like Docker, Neon or Vercel.

Happy coding!