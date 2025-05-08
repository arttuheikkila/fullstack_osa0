sequenceDiagram
    participant browser
    participant server

    Note over browser: User types note and clicks "Save"
    browser->>browser: JS intercepts form submit, prevents default
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/notes (JSON body)
    activate server
    Note right of server: Server validates & stores new note
    server-->>browser: { "id": 42, "content": "Uusi muistiinpano", "date": "2025-05-08" }
    deactivate server

    Note right of browser: SPA updates internal state with new note
    browser->>browser: Re-render notes list including new note
