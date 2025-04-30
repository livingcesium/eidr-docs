<p align="center">
    <img src="https://img.shields.io/github/license/EIDR-ID/python" alt="License">
</p>

<h1 align="center">EIDR Python SDK</h1>
<p align="center">
  A friendly Python client for the <strong>Entertainment Identifier Registry</strong>—the global unique-ID system for film &amp; TV assets.
</p>

---

## ✨ Features
- **Config file or dictionary** – auto-discovers credentials from `~/.eidr/config`, or pass in a dictionary with your login
- **Rich service objects** – `Query`, `Resolve`, `Register`, `Status`, and more.
- **File IO** for verbose records.
- **Type-Hinted Responses** for common responses, create automated workflows easily!
- **Async** support for operations with non-immediate responses.

---

## 📦 Installation

```bash

git clone https://github.com/EIDR-ID/python.git
cd python
python3 -m venv venv && source venv/bin/activate   # Windows: venv\Scripts\activate
pip install .
```

> **Requires** Python ≥ 3.8

---

## 🏗️ General Workflow (90 % of use-cases)

| Step | Action | Code Snippet |
|------|--------|-------------|
| 1 | **Create** a `SessionManager` (auth & transport) | `session = SessionManager.from_default()` |
| 2 | **Instantiate** a service operation (`Query`, `RegistrationService`, …) | `q = Query(... )` |
| 3 | **Wrap** operations in `RegistryRequest` | `req = RegistryRequest([q])` |
| 4 | **Execute** via `session.query(req)`, `session.register(req)`, etc. | `ids, cont = session.query(req)` |
| 5 | **Follow** continuation tokens for pagination | pass `cont` into the next call |
| 6 | **Resolve** DOIs for detailed metadata | `meta = session.resolve(ids[0])` |
| 7 | **Poll** status for async jobs | `session.status(status_req)` / `session.future_status(...)` |

---

<a href="./start">Get Started!</a>