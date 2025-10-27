# Node.js & Express.js Guide

## 1️⃣ `npm init`

- Initializes a new Node.js project.
- Creates a `package.json` file with project metadata (name, version, dependencies, etc.).
- Command:

```bash
npm init
```

- Shortcut:

```bash
npm init -y
```

- `package.json` helps manage dependencies, scripts, and configurations.

---

## 2️⃣ Entry Point

- Defined in `package.json` under `"main"`.
- Specifies the starting file for your app (e.g., `index.js`, `server.js`).
- Example:

```json
{
  "main": "server.js"
}
```

- In backend apps, this is usually the file that starts the server.

---

## 3️⃣ `npm express`

- Refers to installing or using the Express.js framework via npm.
- Install with:

```bash
npm install express
```

- Express helps build backend servers easily — handles routing, middleware, and APIs.
- Example:

```javascript
const express = require("express");
const app = express();
```

---

## 4️⃣ Port in Server

- A port is a communication endpoint (like a "door" to your computer).
- Each app listens on a specific port for requests.
- Example:

```javascript
app.listen(3000);
```

- Common ports:

| Port        | Usage              |
| ----------- | ------------------ |
| 80          | HTTP               |
| 443         | HTTPS              |
| 3000        | Node.js dev server |
| 5000 / 8000 | Backend APIs       |
| 3306        | MySQL              |
| 27017       | MongoDB            |

---

## 5️⃣ Express Server Example Breakdown

```javascript
const express = require("express");
const app = express();
const port = 3000;

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```

### Explanation

| Code                 | Purpose                         |
| -------------------- | ------------------------------- |
| `require("express")` | Imports the Express library     |
| `express()`          | Creates an Express app instance |
| `const port = 3000`  | Sets the port number            |
| `app.get("/", ...)`  | Defines a GET route for `/`     |
| `res.send()`         | Sends response to the browser   |
| `app.listen(port)`   | Starts the server on that port  |

---

## 6️⃣ Adding More Routes

```javascript
app.get("/second", (req, res) => {
  res.send("Hello Second World!");
});
```

- Adds another GET route at `/second`.
- You can define multiple routes like:

```javascript
app.get("/about", (req, res) => res.send("About Page"));
app.get("/contact", (req, res) => res.send("Contact Page"));
```

---

## ✅ Summary Table

| Concept         | Purpose                                            |
| --------------- | -------------------------------------------------- |
| `npm init`      | Creates `package.json`                             |
| Entry Point     | Defines main file (e.g., `index.js`)               |
| `npm express`   | Installs Express.js framework                      |
| Port            | Communication endpoint (e.g., 3000)                |
| Express Server  | Handles routes and responses                       |
| Multiple Routes | Allows multiple endpoints like `/`, `/about`, etc. |
