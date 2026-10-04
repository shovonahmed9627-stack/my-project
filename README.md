# my-project

Main project repository: a Node.js web server built with Express.

## Features

Currently implemented in `index.js`:

- Express HTTP server with configurable port (`PORT` env variable, default `3000`)
- JSON and URL-encoded request body parsing
- `GET /` returns a welcome message (JSON)
- `GET /health` returns server status and uptime (JSON)
- JSON 404 handler for unknown routes
- Centralized error-handling middleware (returns HTTP 500)

## Architecture

Single-process Node.js application. Requests pass through these layers in order:

Client -> Express app -> Body parsers -> Route handlers -> 404 handler -> Error handler -> JSON response

| Layer | Purpose |
|---|---|
| Middleware | `express.json()` and `express.urlencoded()` parse request bodies |
| Routes | `/` and `/health` endpoints |
| 404 handler | Returns `{ "error": "Not Found" }` for unmatched routes |
| Error handler | Logs the error and returns `{ "error": "Internal Server Error" }` |

### Project structure

- `index.js`: Express server entry point
- `.gitignore`: Node.js ignore rules
- `LICENSE`
- `README.md`

## Getting started

**Prerequisites:** Node.js (LTS) and npm.

```bash
git clone https://github.com/shovonahmed9627-stack/my-project.git
cd my-project
npm init -y
npm install express
node index.js
```

Verify: open http://localhost:3000/health. Expected response: `{ "status": "ok", "uptime": 1.23 }`

## Roadmap

Not yet implemented. Add planned features here as they are decided.

## License

See [LICENSE](LICENSE).