# Privilege Escalation

The example demonstrates a privilege escalation vulnerability and how to exploit it.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Start the **insecure.ts** server

    `$ npx ts-node insecure.ts`

3. In the browser, send a GET request

    ```
        http://localhost:3000/send-form
    ```

4. Try different UserIds and see which one gives you authorized access to change the role of that user.

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
userId in the update-role route is being read from an untrusted source.
2. Briefly explain how a malicious attacker can exploit them.
Because matching Id is the only method of authentication, anyone who knows the userId of an admin role can change that account's role to whatever they want.
3. Briefly explain the defensive techniques used in **secure.ts** to prevent the privilege escalation vulnerability?
The secure version implements an authentication step, ensuring that only someone who knows both the Id and password (a.k.a, the account holder) can change an account's role.