---
title: "Complete Auth JS guide for Next.js"
seoTitle: "Krish Desai Next.js Authentication: A Complete Guide"
seoDescription: "Integrate NextAuth.js in Next.js with this step-by-step guide on essential concepts and configuration strategies"
datePublished: Thu Mar 06 2025 09:17:16 GMT+0000 (Coordinated Universal Time)
cuid: cm7x4v14y001709l1dgyc6nkn
slug: complete-auth-js-guide-for-nextjs
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1741245113344/32eb77b8-9fa3-42f6-9bee-17beedd82327.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1741494616290/7684bc91-1db1-4faa-8ca8-380a54d96a5e.jpeg

---

### This post provides a detailed, step-by-step guide to implementing NextAuth.js (previously known as Next Auth) in your Next.js projects. It covers the essential concepts and strategies involved.

---

## **Prerequisites :**

* **Next.js knowledge :** This guide assumes you have a basic understanding of Next.js
    
* **TypeScript (Optional) :** While not mandatory, TypeScript is used in the examples
    

---

## **Step-by-Step Implementation**

1. **Install NextAuth.js :**
    
    ```bash
    npm install next-auth
    ```
    
2. **Define Types (TypeScript) :**
    
    When using TypeScript, you can define the types for sessions and users by creating interfaces for the session and user objects. Here's an example:
    

To create a `next-auth.d.ts` file in your project root directory, follow these steps:

1. **Navigate to your project root directory** : Use your terminal or file explorer to go to the root directory of your Next.js project.
    
2. **Create the file** : Create a new file named `next-auth.d.ts`.
    
3. **Define the types** : Add the following TypeScript definitions to the file to extend the default NextAuth.js types
    

```javascript
import NextAuth from "next-auth";

declare module "next-auth" {
  interface User {
    id: string;
    role: string; // e.g., 'admin', 'user'
  }

  interface Session {
    user: User;
    expires: string; // ISO date string
  }
}
```

3. **Configure NextAuth.js Options :**
    

Create a file, such as auth.ts or auth.js, to configure NextAuth.js. The configuration includes

---

* ***Providers* :** An array of authentication providers. This example focuses on the **Credential Provider**. Other providers like Google, Apple, or Discord can also be used by specifying the client ID and secret
    
* ***Credentials* :** Defines the fields to be taken from the user, such as email and password
    
* ***Authorize* :** A function that contains the logic for validating user credentials. It checks if the user exists in the database and verifies the password. Upon successful authentication, it returns user information like ID, email, and role
    
* ***Callbacks* :** Functions that are executed during different stages of the authentication process. The most commonly used callbacks are **session** and **JWT**
    
    * ***Session Callback* :** This is used to transfer information from the server-side to the client-side. Extract user information (ID, role) from the token and add it to the session
        
    * ***JWT Callback* :** Used to add user information to the JWT token. This token can then be used in middleware for authentication
        
* ***Pages* :** Define custom pages for sign-in, sign-out, and error handling.
    
* ***Session Strategy* :** Set the strategy to JWT
    

**Secret :** A secret key used to encrypt the session

```javascript
import { NextAuthOptions } from "next-auth";
import CredentialsProvider from "next-auth/providers/credentials";

export const authOptions: NextAuthOptions = {
  providers: [
    CredentialsProvider({
      name: "Credentials",
      credentials: {
        email: { label: "Email", type: "text" },
        password: { label: "Password", type: "password" },
      },
      async authorize(credentials) {
        // Write a code for authorize user
      },
    }),
  ],
  callbacks: {
    async jwt({ token, user }) {
      if (user) {
        token.id = user.id;
      }
      return token;
    },
    async session({ session, token }) {
      if (session.user) {
        session.user.id = token.id as string;
      }
      return session;
    },
  },
  pages: {
    signIn: "/login",
    error: "/login",
  },
  session: {
    strategy: "jwt",
    maxAge: 30 * 24 * 60 * 60,
  },
  secret: process.env.NEXTAUTH_SECRET, // nextAuth Secret Key
};
```

### Diagram :

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1741252022333/48e084f7-face-47bd-96a2-d89553dceebf.png align="center")

**4\. Create API Endpoint :**

Create a file ***\[...nextauth\].ts*** inside the *pages/api/auth* directory. This file handles the authentication routes. Import the Next Auth function and pass the configuration options

5\. **Register User :**

NextAuth.js is primarily for authentication, not registration. Implement a custom registration strategy using a credential provider. In the registration logic, check if the user already exists, and if not, create a new user in the database

* **Implement Middleware :**
    
    Middleware protects routes based on user roles. Use the [with Auth middleware](https://next-auth.js.org/configuration/nextjs#wrap-middleware) for easy implementation. The with Auth middleware has two parts: middleware and callback. The middleware function will only be invoked if the authorized callback returns true.
    
    ◦ ***Authorize Callback* :** This callback determines whether a user is authorized to access a specific
    
    route. It checks the user's role against the required role for the route.
    
    ◦ ***Middleware* :** If the authorized callback returns true, the middleware is executed, allowing the user to proceed. If false, NextAuth.js handles the redirection to the sign-in page
    

---

### **Key Concepts**

* ***Sessions Vs JWT* :** Sessions store data on the server-side, while JWT store data on the client-side. JWTs eliminate the need to query the database for every request
    
* ***Token in Session* :** The session also has a token; therefore, it is necessary to differentiate between the session token and the JWT token
    
* ***Role-Based Access Control (RBAC)* :** Protecting routes based on user roles
    

---

### **Conclusion**

This guide provides a comprehensive overview of implementing NextAuth.js for authentication in Next.js applications. Remember that NextAuth.js handles authentication, while user registration requires a custom implementation

For Collaboration, Mail me at [**krishdesai044@gmail.com**](mailto:arindammajumder2020@gmail.com)

Thank you : )

![Thank You](https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExYnpiYmJiOHoweXY2Y3h0ZTk3enk2ZHduMTRkZGQ4a2ZrbHZnazVsdyZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/RipfZWzjUDH25euMpM/giphy.gif align="center")