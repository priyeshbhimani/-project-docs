# Security Requirements — ALL must be implemented
  Auth: JWT 1hr, refresh tokens rotate, bcrypt 12 rounds,
    email verify required, max 5 failed logins/IP/15min
  API: helmet(), CORS logocraftai.com only,
    rate limit 100/15min global + 3/min on /generate,
    Zod validation ALL inputs, API keys bcrypt hashed
  Database: RLS all tables, service key backend only
  Files: PNG/JPEG/WebP/SVG only, 10MB max, sanitize SVGs
  Infra: All traffic Cloudflare, WAF on, Bot Fight on, HTTPS only
  Frontend: No JWT in localStorage, no dangerouslySetInnerHTML
  
