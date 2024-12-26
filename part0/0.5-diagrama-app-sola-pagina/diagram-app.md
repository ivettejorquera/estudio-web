```mermaid

sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinkifi/exampleapp/spa.js
    activate server
    server->>browser: the JavaScript file
    deactivate server

    Note right of browser: El navegador ejecuta el JAvaScript que construye dinamicamente la interfaz

    browser->>server: GET https://studiescshelsinki.fi/exampleapp/data.json
    activate server
    server->>browser: JSON con las notas [{ "content": "SPA note", "date": "2024-12-26" }, ...]
    deactivate server

    Note right of browser: El navegador utiliza el JSON para renderizar las notas sin recargar la pagina