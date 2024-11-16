# Spoofing

This example demonstrates spoofind through two ways -- Stealing cookies programmatically and cross site request forgery (CSRF).

## Steps to reproduce the vulnerability

1. Install dependencies

    `$ npx install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. Start the malicious server **mal.ts**

    `npx ts-node mal.ts`

4. Open __http://localhost:8000__ in a browser, type a name and Submit.

5. Open the __Application__ tab in the Browser's inspect pane. Find the __Cookies__ under __Storage__. You should see a __connect.sid__ cookie being set.

6. Open the HTML file __mal-steal-cookie.html__ file in the same browser (different tab). Open inspect and view the console.

7. Click the link in the HTML file. Do you see the cookie being stolen in the console?

8. Open the HTML file __mal-csrf.html__ file in the same browser (different tab). What do you see if the user has not logged out of **insecure.ts**? What do you see if the user has logged out? 


## For you to answer

1. Briefly explain the spoofing vulnerability in **insecure.ts**.
The session secret is stored as an insecure cookie in the browser, meaning that a malicious program running on a client's computer
can steal it and make requests while pretending to be the original client by using the session secret.
2. Briefly explain different ways in which vulnerability can be exploited.
Depending on what the access token allows the client to do, an attacker can use the token to retrieve personal information or execute
harmful operations on the server.
3. Briefly explain why **secure.ts** does not have the spoofing vulnerability in **insecure.ts**.
The secure version marks the cookie as http only and limits the cookie to a single domain, meaning that an attacker can't steal it 
programatically, and even if they did, it wouldn't be trusted as it would be coming from a different domain.