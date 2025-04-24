# Project0.4


```mermaid
sequenceDiagram
    participant User
    participant browser
    participant server
    User->>browser: Uses the botton save
    browser->>server: User input
    #is an HTTP POST request to the server address new_note. The server responds with HTTP status code 302. This is a URL redirect,the server asks the browser to perform a new HTTP GET request to the address defined in the header's Location - the address notes.
    browser->>server: HTTP POST /new_note, the browser to perform a new HTTP GET
    server-->>browser: 302 redirect
    Note right of browser: The server responds with HTTP status code 302. This is a URL redirect
    browser->>server: HTTP GET /notes
     #So, the browser reloads the Notes page. The reload causes three more HTTP requests: fetching the style sheet (main.css), the JavaScript code (main.js), and the raw data of the notes (data.json).
    server-->>browser: Reload Page
    Note right of browser: The reload causes three more HTTP requests
    activate server
    browser->>server:  HTTP GET main.css
    server-->>browser: main.css
    deactivate server
    activate server
    browser->>server:  HTTP GET main.js
    server-->>browser: main.js
    deactivate server
    activate server
    browser->>server:  HTTP GET data.json
    server-->>browser: data.json
    deactivate server
