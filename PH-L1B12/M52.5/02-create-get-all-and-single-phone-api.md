# Nodemon & Express Phones API Guide

## 🧩 What is Nodemon?

- A tool that automatically restarts Node.js server when files change.
- Used during development to save time — no manual restarts needed.
- Run your app using:

```bash
nodemon app.js
```

instead of `node app.js`.

---

## 💻 Express Server Example (Phones API)

Main idea: Create a simple API using Express with three routes.

### Code Overview:

```javascript
const express = require("express");
const app = express();
const port = 5000;

const phones = [
  { id: "1", name: "iPhone 15" },
  { id: "2", name: "Galaxy S24" },
];

app.get("/", (req, res) => res.send("Server running!"));
app.get("/phones", (req, res) => res.send(phones));
app.get("/phones/:id", (req, res) => {
  const id = req.params.id;
  const phone = phones.find((p) => p.id === id) || {};
  res.send(phone);
});

app.listen(port, () => console.log(`Server on port ${port}`));
```

### Key Concepts:

- `app.get()` → defines GET routes.
- `req.params.id` → retrieves the ID from the URL (like `/phones/2`).
- `res.send()` → sends data or text to the client.
- `.find()` → searches the array for matching data.
- `app.listen()` → starts the server.

---

## ⚡ In Summary

| Concept    | Explanation                                   |
| ---------- | --------------------------------------------- |
| Nodemon    | Auto-restarts server on file save             |
| Express    | Node.js framework to build web servers easily |
| Route      | Defines how app responds to different URLs    |
| req.params | Access dynamic URL data                       |
| res.send   | Send response to client                       |
