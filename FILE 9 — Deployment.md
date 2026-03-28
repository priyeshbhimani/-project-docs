# Deployment Configuration
  Frontend → Vercel: build=npm run build, output=dist, node=20.x
    Domain: logocraftai.com
    Env: VITE_SUPABASE_URL, VITE_SUPABASE_ANON_KEY, VITE_API_URL,
         VITE_CLOUDINARY_CLOUD_NAME, VITE_STRIPE_PUBLISHABLE_KEY, VITE_RAZORPAY_KEY_ID
    vercel.json: { rewrites:[{source:'/(.*)',destination:'/index.html'}] }
  
  Backend → Railway: start=node src/app.js, node=20.x
    Domain: api.logocraftai.com | Health: GET /health → {status:'ok'}
  
  Cloudflare: A record @→Vercel | CNAME api→Railway URL
    SSL: Full(strict) | Always HTTPS: ON | WAF: ON | Bot Fight: ON
  
  Go-Live Checklist:
  [ ] Env vars in Vercel + Railway | [ ] Supabase SQL run + RLS on
  [ ] Cloudflare DNS + SSL | [ ] Stripe + Razorpay webhooks tested
  [ ] Full user flow tested | [ ] Mobile tested | [ ] Sentry connected
  [ ] Privacy Policy + Terms live | [ ] npm audit clean

