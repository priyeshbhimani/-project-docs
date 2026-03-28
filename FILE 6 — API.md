# API Specification
  Base: https://api.logocraftai.com | Auth: Bearer {jwt} | API: X-API-Key
  
  POST /api/auth/signup     { email, password, full_name }
  POST /api/auth/login      { email, password }
  POST /api/auth/logout
  POST /api/auth/reset-password  { email }
  
  POST /api/logo/generate   { brandName, industry, style, colorMood, tagline }
    → validate → check limit → promptBuilder() → DALL-E 3 ×4 parallel
    → Cloudinary upload → Supabase save → return [{id,imageUrl,thumbnailUrl}]
    Free: 3/day | Pro: unlimited | Error 429 if limit hit
  
  POST /api/logo/regenerate { originalLogoId, feedback }
  GET  /api/logo/history    ?page=1&limit=20
  GET  /api/logo/:id | DELETE /api/logo/:id | PUT /api/logo/:id/favorite
  
  POST /api/animation/generate { logoId, animationStyle }  [Pro only]
  POST /api/animation/export   { animationId, format(gif|mp4|lottie), resolution }
  
  POST /api/brand/generate-palette  { logoId } → node-vibrant colors
  POST /api/brand/suggest-fonts     { style, industry } → 3 pairings
  POST /api/brand/create-kit        { logoId, colors, fonts, kitName }
  GET  /api/brand/kits
  
  POST /api/payment/stripe/checkout   { planId, billing(monthly|annual) }
  POST /api/payment/stripe/webhook    [Stripe sig verified]
  POST /api/payment/razorpay/order    { planId, billing }
  POST /api/payment/razorpay/verify   { order_id, payment_id, signature }
  GET  /api/payment/portal
  
  POST /v1/logo/generate  [Developer API — 5 credits]
  GET  /v1/account/credits | GET /v1/account/usage
  
  Error: { error:true, code:'ERR_CODE', message:'...', upgrade_url:'...' }

