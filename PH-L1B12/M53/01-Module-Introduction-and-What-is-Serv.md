# 🧠 Backend Engineering – Server & API Notes

## ⚙️ 1. What Is a Server?
A server is a computer or program that provides services or data to clients such as browsers or mobile apps. It listens for incoming requests, runs the required logic, and returns results.

## 🌐 2. Why Does a Server Need to Work 24/7?
- Users access applications across time zones, so requests never stop.
- APIs and background jobs need constant availability to stay reliable.
- Downtime erodes user trust, reduces revenue, and can break integrations.
- Modern systems rely on cloud redundancy, load balancers, and automated failover to maintain uptime.

## 🔁 3. Data Flow Between Client, Server, and API
Client → API Request → Server → Business Logic → Database → Response → Client

1. Client sends an HTTP request (GET, POST, etc.).
2. Server receives and validates the request.
3. Business logic executes on the server.
4. Database is queried or updated.
5. Server returns a response—often JSON.
6. Client updates the UI based on the response.

## 🧱 4. Types of Servers
| Server Type         | Function                                  | Examples                     |
| ------------------- | ----------------------------------------- | ---------------------------- |
| Web Server          | Handles HTTP requests and serves content  | Nginx, Apache                |
| Application Server  | Runs backend code and business logic      | Express.js, Django, Spring   |
| Database Server     | Stores and retrieves structured data      | MySQL, PostgreSQL, MongoDB   |
| File Server         | Manages file storage and sharing          | FTP, NAS, Amazon S3          |
| Mail Server         | Sends and receives email                  | Postfix, Microsoft Exchange  |
| Proxy Server        | Mediates traffic for security/performance | Nginx, HAProxy, Squid        |
| DNS Server          | Resolves domains to IP addresses          | Cloudflare DNS, Google DNS   |
| Cloud Server        | Virtualized server hosted in the cloud    | AWS EC2, GCP Compute, Azure  |

## 🧩 5. How Servers Work Together (Example Flow)
```
Client → Web Server → Application Server → Database Server
                      ↳ File Server (media assets)
                      ↳ Mail Server (notifications)
```
Example flow:
1. User submits login form.
2. Web server routes the request to the application server.
3. Application server validates credentials.
4. Database confirms user records.
5. Mail server sends a login notification email.

## 🗄️ 6. Common Server Protocols
- HTTP/HTTPS: Web communication
- FTP/SFTP: File transfers
- SMTP/IMAP/POP3: Email delivery and retrieval
- TCP/IP: Foundational internet transport

## 🧠 7. Summary
- Servers stay online continuously to respond to clients.
- Each server type handles a focused responsibility.
- Combined, servers form the backend ecosystem powering modern applications.
