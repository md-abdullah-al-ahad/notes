# Express.js Server Notes

## Overview

A basic Express.js web server that responds with "Hello World!" when accessed.

---

## Code Breakdown

### 1. Import and Initialize Express

```javascript
const express = require("express");
const app = express();
```

- **`require('express')`** - Imports the Express framework
- **`express()`** - Creates an Express application instance

### 2. Configure Port

```javascript
const port = 3000;
```

- Defines the port number the server will listen on
- Port 3000 is commonly used for local development

### 3. Define Routes

```javascript
app.get("/", (req, res) => {
  res.send("Hello World!");
});
```

- **`app.get(path, callback)`** - Defines a route for GET requests
- **`'/'`** - Root path (homepage)
- **`req`** - Request object (contains info about the HTTP request)
- **`res`** - Response object (used to send responses back)
- **`res.send()`** - Sends the response to the client

### 4. Start the Server

```javascript
app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

- **`app.listen(port, callback)`** - Starts the server
- Listens for incoming connections on the specified port
- Callback executes when server starts successfully

---

## How It Works

1. Server starts and listens on `http://localhost:3000`
2. When a user visits the root URL (`/`), the server receives a GET request
3. The route handler executes and sends "Hello World!" as the response
4. The browser displays "Hello World!"

---

## Key Concepts

### HTTP Methods

- **GET** - Retrieve data from server (used here)
- **POST** - Send data to server
- **PUT** - Update existing data
- **DELETE** - Remove data

### Request Object (req)

Contains information about the HTTP request:

- `req.params` - URL parameters
- `req.query` - Query string parameters
- `req.body` - Request body data
- `req.headers` - HTTP headers

### Response Object (res)

Methods to send responses:

- `res.send()` - Send various types of responses
- `res.json()` - Send JSON response
- `res.status()` - Set HTTP status code
- `res.render()` - Render a view template

---

## Running the Server

1. Install Express: `npm install express`
2. Save code to a file (e.g., `server.js`)
3. Run: `node server.js`
4. Visit: `http://localhost:3000`

---

## Next Steps

- Add more routes (e.g., `/about`, `/contact`)
- Handle different HTTP methods (POST, PUT, DELETE)
- Add middleware for parsing JSON, handling errors
- Serve static files (HTML, CSS, images)
- Connect to a database
- Implement authentication
