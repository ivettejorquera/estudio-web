```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: El usuario escribe una nota en el campo de texto y hace clic en el boton save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note left of server: El servidor recibe la nueva nota como JSON
    server-->>browser: Redirección a /notes
    desactive server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    desactive server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: El navegador ejecuta el JavaScript que obtiene el JSON actualizado con las notas

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON actualizado con la nueva nota [{ "content": "Nueva nota ingresada", "date": "2024-12-26" }, ...]
    deactivate server

    Note right of browser: El navegador ejecuta la funcion de callback para renderizar las notas actualizadas