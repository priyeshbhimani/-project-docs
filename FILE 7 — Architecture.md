# System Architecture
  USER → CLOUDFLARE (DDoS+WAF+CDN+SSL)
           ├── VERCEL → logocraftai.com (React Frontend)
           └── RAILWAY → api.logocraftai.com (Node.js Backend)
                    ├── SUPABASE (DB + Auth)
                    ├── CLOUDINARY (Images)
                    ├── OPENAI (DALL-E 3)
                    ├── STABILITY AI (Fallback)
                    ├── LOTTIEFILES (Animation)
                    ├── STRIPE + RAZORPAY (Payments)
                    ├── RESEND (Email)
                    └── UPSTASH REDIS (Cache + Rate Limit)
  
  Generation: Form→POST /generate→validate→limit check→promptBuilder
  →DALL-E 3 ×4 parallel→Cloudinary→Supabase→4 URLs→2×2 grid
  
  Animation: Pick style→POST /animation/generate→LottieFiles AI
  →Lottie JSON→preview→POST /export→Puppeteer→ffmpeg→GIF/MP4→download
  
  Payment: Upgrade→Stripe/Razorpay checkout→webhook→update plan→redirect
