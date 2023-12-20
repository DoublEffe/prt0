sequenceDiagram
    participant browser
    participant server
    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa

    Note right of browser: After sending A POST request the javascript in the browser refetch the data updating only the new notes on the page