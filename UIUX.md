# UI/UX Design Specification — Dark, premium, AI-native, 2026
  bg-primary: #0A0F1E | bg-card: #1A1F2E | accent: #4F46E5 | violet: #7C3AED
  text: #F1F5F9 | muted: #94A3B8 | border: rgba(255,255,255,0.08)
  Font: Inter 400/500/700/800 | Border-radius: 16px cards, 12px buttons
  Cards: glassmorphism, hover translateY(-4px) + indigo glow shadow
  Buttons: gradient #4F46E5→#7C3AED, shimmer on hover, scale 1.02
  Animations: Framer Motion page transitions, Lenis smooth scroll
  Scroll: elements fade+slideUp on viewport entry via IntersectionObserver
  Pages: landing(hero+marquee+bento+how+pricing+testimonials)
         generate(step1 form → step2 loading → step3 2×2 grid)
         editor(3-col full-viewport: icons|canvas|properties)
         dashboard(bento logo grid + quick actions)
