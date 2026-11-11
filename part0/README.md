# Part 0 (Fundamentals of Web Apps) Exercises (Sequence Diagrams)

### Exercise 0.4 : New note diagram

```mermaid
    sequenceDiagram
    participant browser
    participant server

    browser->>server : POST https://studies.cs.helsinki.fi/exampleapp/new_note ("note"="redial")
    server->>browser : HTTP Status Code 302 (Location : /exampleapp/notes)
    Note left of server : URL redirect happens where the server asks the browser to make HTTP GET request to address defined in the header's Location
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/notes
    server->>browser : HTML Document
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/main.css
    server->>browser : CSS File
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/main.js
    server->>browser : JS File
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server->>browser : [{"content": "redial", "date": "2026-11-11T03:40:44.784Z"}]
    Note right of browser : JS calls the callback and  updates the list and displays on the webpage


```

---

### Exercise 0.5 : Single page app diagram

```mermaid
    sequenceDiagram
    participant browser
    participant server

    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/spa
    server->>browser : HTML Document
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/main.css
    server->>browser : CSS Document
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    server->>browser : the JavaScript File
    Note right of browser : SPA doesnt reload the page unlike traditional form as the JS modifies the page in place thus url redirect is not required
    browser->>server : GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server->>browser : [{"content": "test", "date": "2026-11-10T16:07:32.162Z"}]
    Note right of browser : JS calls the callback and builds list and displays on the webpage

```

---

### Exercise 0.6 : New note in Single page app diagram

```mermaid
    sequenceDiagram
    participant browser
    participant server

    browser->>server : POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa {"content": "data2", "date": "2026-11-10T16:00:05.441Z"} (Content type : application/json)
    server->>browser : HTTP Status Code 201 created {"message":"note created"}
    Note right of browser : JS adds the note to the webpage without any reload(and refetching of html and css file) or redirect thus making it faster than traditional form

```
