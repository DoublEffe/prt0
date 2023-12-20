sequenceDiagram
    participant browser
    participant server

    Note right of browser: Request to the server for updating the notes

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note

    Note right of browser: Request of the browser of all the necessary file

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    browser->>server: GET chrome-extension://nngceckbapebfimnlniiiahkandclblb/content/fido2/page-script.js
    activate server
    server-->>browser: javascript text
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "22223", date: "2023-12-19T22:43:39.944Z"} , ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the notes 