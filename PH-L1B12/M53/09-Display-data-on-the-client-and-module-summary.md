# M53 — Display data on the client and module summary (notes for items 05–09)

## 05 — What is database / DBMS / MongoDB / NoSQL vs SQL

- Database: organized collection of data stored for retrieval, update and management.
- DBMS (Database Management System): software that provides an interface to create, read, update, delete (CRUD) and manage databases; examples: MySQL, PostgreSQL, MongoDB.
- MongoDB: a popular document-oriented NoSQL database that stores JSON-like documents (BSON). Good for flexible schemas and rapid development.

Key contrasts: NoSQL vs SQL

- Schema: SQL (fixed schema, relational tables) vs NoSQL (schema-less or flexible, documents/keys).
- Scaling: SQL often scales vertically; NoSQL is built for horizontal scaling and sharding.
- Transactions: SQL offers strong ACID guarantees; many NoSQL stores provide eventual consistency or tuned consistency models (MongoDB supports multi-document transactions in modern versions).
- Use cases: SQL for relational data and complex joins; NoSQL for hierarchical/denormalized data, rapid iteration, and high write throughput.

Quick MongoDB examples (shell-like):

- Insert: `db.phones.insertOne({ name: "Phone A", price: 199 })`
- Query: `db.phones.find({ price: { $lt: 300 } })`
- Update: `db.phones.updateOne({ _id: id }, { $set: { price: 179 } })`
- Delete: `db.phones.deleteOne({ _id: id })`

When to pick MongoDB: flexible data, JSON-like objects, fast iteration, or when you expect to shard/scale horizontally.

## 06 — install-node-express (summary of example)

- Purpose: set up a minimal Express server that responds to requests ("Hello World" example).
- Steps (typical):
  1.  `npm init -y` to create package.json
  2.  `npm install express`
  3.  Create `server.js` and require express: `const express = require('express')`
  4.  Create routes, e.g. `app.get('/', (req, res) => res.send('Hello World!'))`
  5.  `app.listen(port, () => console.log(...))`

Key concepts shown in the file:

- `app.get(path, handler)` to handle GET requests
- `req` and `res` objects: `req.params`, `req.query`, `req.body` (body requires middleware), `res.send()`, `res.json()`, `res.status()`
- Starting the server and choosing a port (3000 common for local dev)

Notes / next steps: add `app.use(express.json())` to parse JSON bodies, add more routes (GET/POST/PUT/DELETE), and connect to a database for persistence.

## 07 — Use fetch to load data / create React form

Summary (based on filename): how to fetch data from server and build a form in React to create data.

Key points:

- Use `fetch()` or `axios` in React to call server endpoints. Typical GET pattern with `useEffect`:

  - `useEffect(() => { fetch('/api/phones').then(r => r.json()).then(setPhones) }, [])`

- Displaying data: map over the array and render components, e.g. `phones.map(p => <li key={p._id}>{p.name} — {p.price}</li>)`.
- Building a controlled React form:

  - Maintain state: `const [form, setForm] = useState({ name: '', price: '' })`
  - Update on change: `onChange={e => setForm({ ...form, [e.target.name]: e.target.value })}`
  - Submit handler: `onSubmit={e => { e.preventDefault(); /* send data */ }}`

- On submit, send a POST request with the form data (see item 08 for details on POST):

  - `fetch('/api/phones', { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(form) })`

UX tips: validate inputs, show loading state and success/error feedback, clear form after success.

## 08 — Explore fetch for POST method and send client data to the server

Essential checklist for POST with fetch:

- Request:
  - `fetch(url, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body: JSON.stringify(data) })`
  - Handle the returned promise and JSON: `then(res => res.json()).then(data => ...)`.
- Server-side:
  - Enable JSON body parsing in Express: `app.use(express.json())`
  - Create POST route: `app.post('/api/phones', (req, res) => { const phone = req.body; /* validate & save */ res.status(201).json(saved) })`
- CORS: if client and server run on different origins, enable CORS on server (`npm install cors; app.use(require('cors')())`) or configure proxy in React dev server.
- Error handling: check response status, handle network errors, and show appropriate UI messages.

Security & validation:

- Never trust client data — validate on server (required fields, types, ranges)
- Sanitize if inserting into databases or building queries to avoid injection risks

## 09 — Display data on the client & module summary

Displaying fetched data effectively:

- Loading state: `const [loading, setLoading] = useState(true)` and show spinner/text while loading.
- Error state: `const [error, setError] = useState(null)` and display friendly message on failure.
- Map data to components and use stable keys (e.g., database `_id`).
- Provide empty-state UI when the dataset is empty and include retry or refresh controls.

Module summary / checklist (what this module teaches):

- Understand basic database concepts (DB vs DBMS, NoSQL vs SQL) and MongoDB basics.
- Install and bootstrap an Express server and create simple routes.
- Use `fetch()` to GET data from server and render it in a React component.
- Build a controlled React form to collect user input.
- Use `fetch()` POST to send JSON to the server and parse it with `express.json()`.
- Handle CORS, basic validation, loading/error states, and provide user feedback.

Next recommended steps:

- Connect Express to MongoDB (e.g., using the `mongodb` or `mongoose` package) and persist created resources.
- Add more robust validation (server-side and client-side) and error handling.
- Add unit/integration tests for routes and client interactions.
- Explore deployment (Heroku, Vercel for client, Atlas for MongoDB) and environment configuration.
