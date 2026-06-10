# YES-HA Portfolio — Project Brief
## Paste this at the start of every new Claude chat

---

## WHO YOU ARE TALKING TO
- Yesha Niranjan — Senior Product/UX Designer, 7+ years, AI-first products
- Founder: Mayd Sense Studios LLC, brand "YES-HA"
- Based: Bay Area (South Bay)
- Communication style: Direct, fast, abbreviated. No fluff. No flattery. Be honest.
- Preferred responses: Compact, immediately actionable, show image previews before building

---

## THE SITE
- Domain: yesha.online
- Repo: https://github.com/Yesha2411/website_portfolio
- Local path: ~/yesha-website
- Live URL: https://website-portfolio-xi-seven.vercel.app
- Deployed via: GitHub → Vercel (auto-deploys on push)

---

## PUSH WORKFLOW
```bash
cd ~/yesha-website
cp ~/Downloads/"filename (N).html" filename.html
git add .
git commit -m "message"
git push
```
- macOS names downloaded files with spaces + (N) suffix e.g. `"about (3).html"`
- Always use quotes around filenames with spaces or parentheses
- Vercel deploys in ~20 seconds after push

---

## DESIGN SYSTEM — NEVER DEVIATE
```css
font-family: 'Sora', sans-serif (weights: 300/400/500/600 only)
--white: #ffffff
--black: #111111
--rule: rgba(0,0,0,0.10)
--muted: rgba(17,17,17,0.42)
--chip: #f4f4f4
--sidebar-w: 200px
--toc-w: 220px (case study pages only)
```
- NO other fonts anywhere in UI
- NO Playfair, NO Inter, NO other sans
- Background always #ffffff, ink always #111111
- Page header pattern: 10px uppercase tracked label + count, border-bottom
- Bottom bar: 52px height, border-top, consistent across ALL pages

---

## SIDEBAR (ALL PAGES)
```css
position: fixed; left: 0; width: 200px; border-right: 1px solid var(--rule);
padding: 36px 32px;
```
- Logo: YES-HA (font-weight: 600)
- Nav links: Home / Works / Playground / Hot Takes / About / Connect
- Icons: Email / LinkedIn / Behance (SVGs)
- Toggle button: fixed, left:189px expanded / left:41px collapsed
- Collapsed: 52px rail, logo rotates vertical, nav = dots
- localStorage key: 'sidebarCollapsed'
- EARLY SCRIPT (paste in every page right after `<body>`):
```html
<script>
  (function(){
    var collapsed = localStorage.getItem('sidebarCollapsed') === 'true';
    var style = document.createElement('style');
    if(collapsed){
      style.textContent = '.sidebar{width:52px!important}.sidebar-toggle{left:41px!important}.main{margin-left:52px!important}';
    } else {
      style.textContent = '.sidebar-toggle{left:189px!important}';
    }
    document.head.appendChild(style);
  })();
</script>
```
- Mobile: sidebar hidden, hamburger overlay, breakpoint 900px

---

## PAGES BUILT — STATUS
| File | Status | Notes |
|------|--------|-------|
| index.html | ✅ Live | Hero, typewriter, bottom bar |
| work.html | ✅ Live | 2-col card grid, 6 cards all linked |
| about.html | ✅ Live | Process cards, dark logo strip, floating testimonials |
| connect.html | ✅ Live | Split layout, contact form |
| hot-takes.html | ✅ Live | Pinterest masonry, 6 cards |
| playground.html | ✅ Live | 3-panel interactive, STAR framework, 10 projects |
| lucid.html | ✅ Live | Full case study, 10 sections |
| navigator.html | ✅ Live | 2-chapter (Navigator + Sensei AI) |
| philips.html | ✅ Live | Full case study, 7 sections |
| lead.html | ✅ Live | Full case study, 8 sections |
| oac.html | ✅ Live | Full case study, 7 sections |
| ring.html | ✅ Live | Full case study, 8 sections |
| sensei.html | ⏳ Dummy | Coming soon shell |

---

## CASE STUDY PAGE TEMPLATE RULES
Every case study uses the SAME shell. No exceptions.
- Progress bar: 2px fixed top, fills on scroll
- Hero: black bg, `cs-back` link, tag, title, subtitle, chips, hero image
- Mobile TOC: sticky horizontal pill strip
- Desktop TOC: sticky left column, 220px, active tracking via IntersectionObserver
- Content: 48px 56px padding, sections fade up on scroll
- Pull quotes: slide in from left with 200ms delay
- Bottom bar: ← All Works | Next Case Study (center, prominent) | Connect (pill)
- Image placeholders: `projectname-N.ext` naming convention

### Bottom bar pattern (copy exactly):
```html
<div class="bottom-bar">
  <a class="bottom-back" href="work.html">← All Works</a>
  <a class="bottom-next" href="NEXT.html">
    <span class="bottom-next-label">Next Case Study</span>
    <span class="bottom-next-title">TITLE →</span>
  </a>
  <a class="bottom-connect" href="connect.html">Connect</a>
</div>
```

---

## CASE STUDY CHAIN (navigation order)
lucid → philips → navigator → sensei (dummy) → lead → oac → ring → lucid

---

## IMAGE NAMING CONVENTION
`projectname-N.ext`
- lucid-1.avif through lucid-5.avif
- philips-1.jpg through philips-5.jpg
- navigator-1 through navigator-4, sensei-1 through sensei-2
- lead-1 through lead-5
- oac-1 through oac-5
- ring-1 through ring-5
- Hero images: img-lucid.png, img-philips.jpg, img-navigator.webp, img-sensei.webp, img-lead.png, img-ring.png, img-oac.webp

---

## ABOUT PAGE SPECIFICS
- Process section: 4 cards with images (process-breathe.jpg, process-reflect.jpg, process-experiment.jpg, process-weave.jpg)
- Client logos in dark strip: logo-lucid.svg, logo-philips.png, logo-benesse.png, logo-lead.png, logo-ring.png, logo-morph.png, logo-mercor.png
- Logo CSS: `filter:brightness(0) invert(1); mix-blend-mode:lighten` on dark bg
- Floating testimonials: Carter Jones, Chaitanya Naik, Kazuya Furushima

---

## PLAYGROUND PAGE SPECIFICS
- 3-panel layout: sidebar | project list with filters | detail panel (STAR)
- Filters: All / AI / Health / Creative / Installation
- Mobile: master→detail, ← All Projects back button
- 10 projects with full STAR content

---

## HOW TO BUILD NEW THINGS
1. Always show image preview first (using show_widget visualizer)
2. Wait for approval before building HTML
3. Build → present_files → give push command
4. Never deviate from design system
5. Always include sidebar toggle early script
6. Always mobile responsive (breakpoint 900px and 480px)

---

## BEHANCE SVG (correct path — use this, not the broken one)
```html
<svg viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M7.443 5.35c.639 0 1.23.05 1.77.198.541.099.984.297 1.377.544.394.247.689.594.886 1.039.197.396.296.891.296 1.435 0 .594-.147 1.089-.443 1.484-.295.396-.737.742-1.278 1.039.788.198 1.377.594 1.771 1.138.394.545.59 1.188.59 1.98 0 .594-.099 1.138-.344 1.583-.246.445-.59.84-.983 1.138-.395.297-.886.544-1.427.693-.541.148-1.082.198-1.672.198H0V5.35h7.443zm-.394 5.25c.491 0 .885-.099 1.18-.346.295-.247.442-.594.442-1.089 0-.297-.05-.544-.148-.742-.098-.197-.246-.346-.394-.445-.197-.099-.394-.148-.59-.198-.247-.049-.444-.049-.69-.049H2.95v2.869h4.1zm.197 5.497c.295 0 .541-.049.787-.099.246-.049.492-.148.689-.297.197-.148.394-.346.492-.594.148-.247.197-.545.197-.94 0-.742-.197-1.287-.59-1.583-.394-.297-.935-.445-1.574-.445H2.95v3.958h4.296zm9.76-1.337c.394.395.983.594 1.77.594.541 0 1.033-.148 1.426-.396.394-.247.64-.544.738-.792h2.36c-.394 1.188-.984 2.03-1.77 2.574-.787.495-1.77.742-2.853.742-.787 0-1.475-.099-2.114-.346-.64-.247-1.18-.594-1.623-1.039-.443-.445-.788-.99-1.033-1.633-.246-.643-.345-1.336-.345-2.128 0-.742.099-1.435.345-2.078.246-.643.59-1.188 1.033-1.682.443-.445.984-.84 1.623-1.089.64-.247 1.328-.396 2.065-.396.836 0 1.574.149 2.213.495.64.347 1.132.792 1.524 1.386.394.545.69 1.188.837 1.881.148.693.197 1.436.099 2.178h-7.048c0 .84.295 1.533.787 1.929h-.034zm3.098-5.25c-.344-.395-.886-.594-1.574-.594-.443 0-.836.099-1.132.247-.295.148-.54.346-.688.594-.197.247-.295.495-.344.742-.05.247-.099.445-.099.693h4.789c-.099-.743-.394-1.287-.951-1.682h-.001zM14.89 5.35h5.583v1.287H14.89V5.35z"/></svg>
```

---

## CONTACT INFO (used in pages)
- Email: niranjan.yesha@gmail.com
- LinkedIn: https://www.linkedin.com/in/yesha-niranjan/
- Behance: https://www.behance.net/yeshaniranjan
- CV: https://drive.google.com/file/d/1q6hQW9Sgt5R0IwMWVZdZEZHI0EY9b0ou/view

---

## PENDING WORK
- [ ] sensei.html — full case study (content not yet provided)
- [ ] All case study image placeholders → replace with real images
- [ ] connect.html — Formspree endpoint
- [ ] lucid.html bottom bar: "Next" should point to philips.html

---

*Last updated: June 2026*
