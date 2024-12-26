```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: El usuario escribe unanota y hace click en el boton Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note left of server: El servidor recibe la nueva nota como JSON
    server->>browser: { "message": "note created" }
    deactivate server

    Note right of browser: El navegador actualiza la lista de notas localmente sin recargar la pagina

    browser->>server GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON actualizado con la nueva nota [{ "content": "Nueva nota spa ", "date": "2024-12-26" }, ...]
    deactivate server

    Note right of browser: El navegador renderiza las notas actualizadas en la interfaz