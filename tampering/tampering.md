# Tampering

This example demonstrates tampering through script injection.

## Steps to reproduce

1. Install all dependencies

    `npm install`

2. Start the **insecure.ts** server

    `npx ts-node insecure.ts`

3. In the browser, type a potentially malicious script in the name field of the form

    ```
        <script> document.body.innerHTML = "<a href='https://google.com'> Gotcha </a>"</script>
    ```

4. Do you see the potentially malicious hyperlink being injected into the form?

## For you to do

Answer the following:

1. Briefly explain the potential vulnerabilities in **insecure.ts**
The name input field is not validated - although users are expected to enter strings, a malicious attacker can programtatically set
req.body.name to anything and have the server process it.
2. Briefly explain how a malicious attacker can exploit them.
The server eventually evaluates req.body.name as an expression. If this expression turns out to be a chunk of code, it is executed. This
can be exploited to make the server do basically anything.
3. Briefly explain why **secure.ts** does not have the same vulnerabilties?
The incoming data in req.body.name is sanitized, thus strictly ensuring that it is a string and nothing more.