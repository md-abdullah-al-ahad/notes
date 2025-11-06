# Client & Server Connection with Request & Response

## 1. API vs Server
| Term | Description |
| --- | --- |
| **API (Application Programming Interface)** | Defines how software components communicate (rules, endpoints). |
| **Server** | The machine or program that processes API requests and sends responses. |
| **Client** | Sends requests (browser, app, frontend). |

- Flow: Client → API → Server → Response → Client.
- Analogy: API = waiter/menu 🍽️, Server = kitchen 👨‍🍳, Client = customer 👤.

## 2. REST API (Representational State Transfer)
- A REST API lets systems communicate over HTTP using standard methods.
- Core principles: stateless, client–server separation, uniform interface, cacheable, uses standard HTTP status codes (e.g., 200, 404, 500).

| HTTP Method | Purpose | Example Endpoint |
| --- | --- | --- |
| `GET` | Read data | `/users` |
| `POST` | Create data | `/users` |
| `PUT` / `PATCH` | Update data | `/users/1` |
| `DELETE` | Delete data | `/users/1` |

## 3. Express.js Request (`req`) Object
| Property | Description | Example |
| --- | --- | --- |
| `req.params` | Route parameters | `/users/:id` → `req.params.id` |
| `req.query` | Query string values | `/search?q=node` → `req.query.q` |
| `req.body` | Body payload (JSON/form) | `{ "name": "Ahad" }` |
| `req.headers` | Request headers | `req.headers.authorization` |
| `req.method` | HTTP method | `"GET"`, `"POST"` |
| `req.url` | Full URL path | `"/users/42?sort=desc"` |
| `req.ip` | Client IP address | `"192.168.0.5"` |
| `req.cookies` | Cookies (via middleware) | `{ sessionId: "abc123" }` |

## 4. Express.js Response (`res`) Object
| Method | Purpose | Example |
| --- | --- | --- |
| `res.send()` | Send text/object/HTML | `res.send("OK")` |
| `res.json()` | Send JSON data | `res.json({ user: "Ahad" })` |
| `res.status()` | Set HTTP status code | `res.status(404).send("Not Found")` |
| `res.set()` / `res.header()` | Set headers | `res.set("X-App", "Express")` |
| `res.redirect()` | Redirect client | `res.redirect("/login")` |
| `res.end()` | End response manually | `res.end("Done")` |

## 5. Common HTTP Status Codes
| Code | Meaning | Typical Usage |
| --- | --- | --- |
| `200` | OK | Successful `GET` |
| `201` | Created | Resource created |
| `400` | Bad Request | Invalid input |
| `401` | Unauthorized | Missing/invalid token |
| `404` | Not Found | Resource absent |
| `500` | Internal Server Error | Server crash or logic error |

## 6. Full Flow Example
```js
app.post("/users/:id", (req, res) => {
  if (!req.body.name) {
    return res.status(400).json({ error: "Name required" });
  }

  res
    .status(201)
    .set("X-App", "Express")
    .json({
      message: "User created",
      id: req.params.id,
      name: req.body.name,
    });
});
```

## Quick Summary
- API = communication rules.
- Server = processes requests.
- REST API = HTTP CRUD operations.
- `req` carries data from the client.
- `res` delivers data back to the client.
