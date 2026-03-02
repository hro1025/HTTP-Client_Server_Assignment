# Async Status Probe — HTTP Client/Server Assignment

---

## 📌 Disclaimer & Evaluation Rules

> **Disclaimer**
>
> This assignment was custom-created by ChatGPT as a personal learning exercise.
>
> The requirements, scope, and evaluation criteria are defined **exclusively** in this README.
>
> ChatGPT acts as the grader, and the submission will be evaluated **only** against the criteria described here.
>
> No external rubrics, expectations, or implied requirements apply.

### Grading Rules

- The assignment is graded on **understanding and correctness**, not size or polish
- The focus is on **async behavior, HTTP communication, and reasoning**
- Partial solutions are acceptable if reasoning is clearly demonstrated
- Console output is sufficient for all observations

---

## 🧪 Final Verdict (Grading)

> **Status:** ⏳ Pending  
> **Final Grade:** ⏳ To be determined

This section will be filled **after submission**, based strictly on the criteria in this README.

---

## 📘 Assignment Specification

### Overview

This assignment focuses on understanding **asynchronous HTTP communication** in C# by building a **small client–server system** using:

- `HttpListener` (server)
- `HttpClient` (client)
- `async` / `await`

The goal is **not** to build a production-ready web server, but to understand:

- How HTTP requests and responses behave
- How async execution affects timing and order
- The difference between **sequential** and **parallel** HTTP calls
- How client and server interact asynchronously

---

## 🎯 Learning Goals

By completing this assignment, you should be able to:

- Explain the **client–server relationship**
- Use `HttpListener` to receive and respond to HTTP requests
- Use `HttpClient` to send HTTP requests asynchronously
- Observe differences between **blocking**, **sequential async**, and **parallel async** execution
- Reason about **behavior and timing**, not just syntax

---

## 📦 Scope & Constraints

### In scope (graded)
- `HttpListener`
- `HttpClient`
- `async` / `await`
- Pure C# (.NET)
- Console output for observation

### Out of scope (not graded)
- ASP.NET / WebApplication
- MVC / Controllers
- Dependency Injection
- UI frameworks
- Databases

> You must work directly with `HttpListener` and `HttpClient`.

---

## 🧠 Domain Problem

You will build:

1. A **small HTTP server** that exposes simple endpoints  
2. A **client** that calls these endpoints  
3. Logic that compares **how requests behave** when executed differently

The system answers the question:

> **“What actually happens when I send multiple HTTP requests asynchronously?”**

---

## Part 1 — Minimal HTTP Server

Create a small HTTP server using `HttpListener`.

### Requirements
- The server must listen on `http://localhost:9000/`
- It must support **at least two endpoints**:
  - `/fast`
  - `/slow`

### Behavior
- `/fast` responds immediately with a short text message
- `/slow` waits for a short delay (e.g. 500–1000 ms) before responding
- The delay **must be asynchronous**

---

## Part 2 — HTTP Client

Create a client using `HttpClient`.

### Requirements
- Use **one long-lived HttpClient instance**
- Create a method that:
  - Sends a GET request to a given endpoint
  - Awaits the response
  - Prints:
    - URL
    - Status code
    - Response body

This method represents **one HTTP call**.

---

## Part 3 — Sequential Execution

Call the server endpoints **sequentially**.

### Scenario
- Call `/slow` three times
- Await each request **before** starting the next

### Requirements
- Measure total execution time
- Print timing results

---

## Part 4 — Parallel Execution

Call the same endpoints **in parallel**.

### Requirements
- Start all requests first
- Await them together using `Task.WhenAll`
- Measure total execution time
- Print timing results

---

## Part 5 — Observation & Reasoning

Answer the following questions **in comments or a separate markdown file**:

1. Why is parallel execution faster for I/O-bound work?
2. Why does the server remain responsive with multiple requests?
3. What would happen if blocking calls were used instead of async ones?
4. Why should `HttpClient` be reused?

There are no single “correct” answers — the goal is **reasoned understanding**.

---

## Part 6 — Edge Case Exploration

Choose **one** edge case:

- Request an endpoint that does not exist (`/unknown`)
- Shut down the server and observe client behavior
- Force the server to return a non-200 status code

### Requirements
- Handle the case gracefully
- Do not crash the program
- Print meaningful output

---

## ✅ Success Criteria

You have completed the assignment when:

- A working `HttpListener` server exists
- A working `HttpClient` client exists
- Sequential vs parallel behavior is observable
- All HTTP calls are asynchronous
- One edge case is handled intentionally
- You can explain **why** the observed behavior happens
