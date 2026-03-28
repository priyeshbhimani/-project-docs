# Database Schema — Supabase PostgreSQL
  TABLE profiles: id UUID PK→auth.users, full_name, avatar_url,
    plan(free|pro|business|api), stripe_customer_id, razorpay_customer_id,
    daily_gen_count INT DEFAULT 0, daily_gen_reset DATE, created_at
  
  TABLE logos: id UUID PK, user_id FK, brand_name NOT NULL, industry,
    style, color_mood, tagline, prompt_used, image_url NOT NULL,
    svg_url, thumbnail_url, is_favorite BOOL, project_name, created_at
  
  TABLE animated_logos: id UUID PK, logo_id FK, user_id FK,
    animation_style, lottie_json JSONB, gif_url, mp4_url, resolution INT
  
  TABLE brand_kits: id UUID PK, user_id FK, logo_id FK, kit_name,
    primary_color, secondary_color, accent_color, neutral_color,
    font_primary, font_secondary, pdf_url, share_token UNIQUE
  
  TABLE api_keys: id UUID PK, user_id FK, key_hash TEXT UNIQUE,
    key_prefix TEXT, name, environment(live|test), credits INT, total_calls INT
  
  TABLE subscriptions: id, user_id FK, stripe_sub_id, razorpay_sub_id,
    plan, status, current_period_end TIMESTAMPTZ
  
  TABLE usage_logs: id, user_id FK, action(generate|animate|export|api_call),
    details JSONB, ip_address, created_at
  
  TABLE templates: id, name, industry, style, tags TEXT[], svg_content,
    thumbnail_url, is_premium BOOL, downloads INT
  
  RULES: RLS on ALL tables. Users see only their own rows (user_id=auth.uid()).
  TRIGGER: on auth.users INSERT → auto-create profiles row.
  DAILY CRON: reset daily_gen_count=0 for all free users.
