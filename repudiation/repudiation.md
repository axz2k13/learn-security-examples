# Repudiation

The example demonstrates a vulnerability that can lead to repudiation by malicious users attempting to access the services provided by a server.

## Steps to reproduce

1. Install all dependencies

    `$ npm install`

2. Run the server __insecure.ts__.

3. Pretend to be a malicous user and interact with the services by sending requests from the browser.

4. Do you think your actions can be repudiated?

## For you to do

1. Briefly explain the vulnerability.
The insecure version doesn't keep any kind of record as to what actions were taken by what user.
2. Briefly explain why the vulnerability is addressed in __secure.ts__.
Adding logging is important because it facilitates recovery efforts in case something goes wrong. For example, if a user deletes messages, logging would enable you to see who did it and what they deleted.
3. Which design pattern is used in the secure version to address the vulnerability? Briefly explain how it works?
A chain of responsibility ensures that all actions flow through a middleware function that logs everything. No request can reach code that edits the database without being logged first.