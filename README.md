```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: Пользователь пишет заметку Vladislav и нажимает кнопку Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: HTTP-статус 302 Found 
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML-документ страницы
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Файл стилей main.css
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: Файл скрипта main.js
    deactivate server

    Note over browser: Браузер выполняет JS-код, который запрашивает данные JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Данные заметок в формате JSON
    deactivate server

    Note over browser: Браузер отрисовывает обновленный список заметок на экране
```

## Задание 0.5: Single page app diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML-код 
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: Файл стилей main.css
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: Файл скрипта spa.js
    deactivate server

    Note over browser: Браузер запускает spa.js, который сразу запрашивает чистые данные

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Данные заметок в формате JSON
    deactivate server

    Note over browser: Скрипт spa.js динамически создает элементы списка и выводит их на экран
```
