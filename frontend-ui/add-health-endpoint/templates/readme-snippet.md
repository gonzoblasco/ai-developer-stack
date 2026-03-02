## Health Check

This application includes a minimal health check endpoint at `/health`.

To verify the endpoint is working, run the development server:

```bash
npm run dev
# or yarn dev / pnpm dev
```

Then in another terminal run:

```bash
curl -i http://localhost:3000/health
```

Expected output:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"ok":true}
```
