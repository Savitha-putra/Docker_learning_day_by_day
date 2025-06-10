# 🚀 Redis Overview

**Redis** (REmote DIctionary Server) is an open-source, in-memory key-value data store, widely used for building high-performance, scalable applications.

---

## 🔧 What Is Redis?

Redis is a lightning-fast, in-memory data structure store used as:

- A **cache**
- A **database**
- A **message broker**
- A **session store**

It supports various data types such as strings, hashes, lists, sets, sorted sets, streams, bitmaps, and more.

---

## 💡 Why Use Redis?

### ⚡ Fast Caching
- All data is stored in memory (RAM), enabling sub-millisecond latency.
- Perfect for caching API responses, frequently accessed database queries, etc.

### 🧠 Versatile Data Structures
Redis supports:
- **Strings**: Basic key-value pairs
- **Lists**: Useful for queues
- **Hashes**: Ideal for storing objects
- **Sets** & **Sorted Sets**: For unique and ranked data
- **Streams**: For event-based architectures

### 🔁 Pub/Sub Messaging
- Supports publish-subscribe pattern.
- Helps decouple services in microservice-based systems.

### 📦 Session Storage
- Commonly used to store user session data in web apps (e.g., login tokens).

### ⏳ Expiring Keys (TTL)
- Redis allows keys to expire after a defined time — great for temporary data like OTPs or rate limiting.

---

## 🌍 Common Use Cases

| Use Case         | Description                             |
|------------------|-----------------------------------------|
| Caching          | Reduce load on primary databases         |
| Session Store    | Track user sessions in web applications |
| Real-time Metrics| Track analytics and counters             |
| Message Queue    | Basic task queues or event pipelines     |
| Leaderboards     | Real-time sorted scoreboards             |

---

## 🛠 Used By

- **Twitter**
- **GitHub**
- **Pinterest**
- **Netflix**
- **StackOverflow**

---

## 📥 Install Redis (Local)

```bash
docker run --name redis -p 6379:6379 -d redis
```
