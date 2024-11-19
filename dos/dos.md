# Denial-of-Service (DoS)

This example demonstrates DoS vulnerabilities and how they can be exploited.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Ignore if you have already done this once. Insert test data in the MongoDB database. Make sure the mongod is up and running by typing the `mongosh` command in the termainal. If mongod process is up then you will see that the connection was successful. Command to insert test data:

    `$ npx ts-node insert-test-users.ts`

This will create a database in MongoDB called __infodisclosure__. Verify its presence by connecting with mongosh and running the command `show dbs;`.

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, pretend to be a hacker and type a malicious request

    ```
        http://localhost:3000/userinfo?id[$ne]=
    ```

4. Do you see the server crashing?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts** that can lead to a DoS attack.
When casting id as a string, if id isn't a string or User.findOne throws an error, there is no catch statement. The _id field needs to match MongoDBs id formatting rules or an error will be thrown.
2. Briefly explain how a malicious attacker can exploit them.
If the user provides an invalid id, the uncaught exception will crash the entire server.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the DoS vulnerability?
A simple try catch block prevents an error in findOne from crashing the entire server.