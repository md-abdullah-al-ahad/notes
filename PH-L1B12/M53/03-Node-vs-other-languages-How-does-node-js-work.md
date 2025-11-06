# 🟢 Node.js & npm — Quick Notes

## ⚙️ What is Node.js

- Open-source, cross-platform JavaScript runtime (built on Chrome's V8 engine)
- Runs JavaScript outside the browser — mainly on the server
- Enables backend programming using JavaScript

### 🔹 Features

- Single-threaded, non-blocking I/O
- Event-driven architecture
- High scalability
- Uses libuv for async operations

---

## ⚙️ What is npm

- **Node Package Manager** — manages external JS libraries (packages)
- Installed automatically with Node.js

### 🔹 Common Commands

```bash
npm init           # Initialize project
npm install <pkg>  # Install package
npm run <script>   # Run custom script
```

---

## 🧩 Node.js Runtime Environment

### Components:

1. **V8 Engine** – Executes JS code
2. **Libuv** – Provides event loop & async I/O
3. **Node APIs** – Access system functions (fs, http, os)
4. **Bindings** – Bridge between JS (V8) & C++ (libuv)
5. **npm** – Installs 3rd-party packages

### Flow:

```
JS Code → V8 → Libuv → OS → Callback → Event Loop
```

---

## 🧵 Single Thread & Blocking Behavior

- Node.js executes all JS in one main thread (event loop)
- **Blocking** → waits for task to finish (e.g., `fs.readFileSync`)
- **Non-blocking** → delegates task, continues execution (e.g., `fs.readFile`)

**✅ Non-blocking = better performance**  
**❌ Blocking = freezes other tasks**

---

## 👷 Worker Threads

- Solve CPU-heavy task blocking issue
- Allow parallel execution of JS in multiple threads
- Communicate via `postMessage()` and `on('message')`

### When to Use:

- CPU-bound tasks (encryption, image processing)
- Keep main thread responsive

---

## 🧭 When to Use Node.js

### ✅ Best for:

- Real-time apps (chat, live updates)
- APIs / Microservices
- Data streaming
- Lightweight, scalable backends
- Proxy servers / API gateways

---

## 🚫 When Not to Use Node.js

### ❌ Avoid for:

- CPU-heavy computation
- Data analytics / ML
- Complex enterprise systems
- Relational DB-heavy apps
- Synchronous logic-heavy systems

---

## ⚡ Summary Table

| Concept             | Description                          |
| ------------------- | ------------------------------------ |
| **Node.js**         | JS runtime for server-side code      |
| **npm**             | Package manager for Node.js          |
| **Single-threaded** | One main event loop for JS execution |
| **Non-blocking**    | Async operations via libuv           |
| **Worker Threads**  | Run heavy computations in parallel   |
| **Use Case**        | Real-time, scalable, I/O-heavy apps  |
| **Avoid For**       | CPU-heavy or computation-heavy apps  |
