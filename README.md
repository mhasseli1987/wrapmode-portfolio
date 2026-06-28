<div align="center">

# 🚗 WrapMode.ir — Full-Stack E-Commerce Platform

**Live:** [wrapmode.ir](https://wrapmode.ir) &nbsp;|&nbsp; **Developer:** Mohammad Haseli &nbsp;|&nbsp; **Stack:** Next.js 16 · TypeScript · PostgreSQL · nginx

[![Next.js](https://img.shields.io/badge/Next.js-16.2-black?style=for-the-badge&logo=next.js)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://neon.tech)
[![Ubuntu VPS](https://img.shields.io/badge/Ubuntu-VPS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com)

</div>

---

## 📌 پروژه چیست؟

**WrapMode** یک فروشگاه آنلاین تخصصی برای فروش **PPF (فیلم محافظ بدنه خودرو)**، **کاور رنگی**، **شیشه دودی** و **ابزار نصب** است.
نماینده رسمی برندهای **Avery Dennison** و **KODAK** در ایران.

این پروژه از **صفر** طراحی، کدنویسی، دیپلوی و بهینه‌سازی شده — توسط یک نفر.

---

## 🏗️ Architecture Overview

```
wrapmode.ir
├── Frontend        Next.js 16 App Router (SSR + SSG)
├── Database        Neon PostgreSQL (serverless)
├── Auth            nginx Basic Auth (admin panel)
├── Server          Ubuntu VPS + PM2 + nginx reverse proxy
├── SSL             Let's Encrypt (Certbot)
└── DNS             Cloudflare
```

---

## ✨ Features Built

### 🛍️ E-Commerce Core

| Feature | Description |
|---|---|
| **Product Catalog** | 150+ products across 6 categories |
| **Shopping Cart** | Persistent cart with Context API, quantity management |
| **Checkout Flow** | Multi-step checkout with address & shipping |
| **Order Management** | Full order lifecycle (pending → confirmed → shipped) |
| **Admin Panel** | Secure dashboard for orders, products, settings |
| **Per-Meter Purchasing** | Custom slider UI for buying PPF by the meter (1m–15m) |

### 🎨 Custom UI Components

| Component | Description |
|---|---|
| **HoverGlowButton** | Animated glow buttons with 5 variants (aurora, pulse, neon, gradient, classic) |
| **HotspotImageSelector** | Click-zone product variant selector on composite images |
| **MeterSlider** | Interactive range slider with real-time price calculation |
| **CircularGallery** | 3D rotating blog gallery (GSAP-powered) |
| **HeroSlider** | Auto-advancing hero with pause-on-hover |
| **ProductCard** | Responsive card with per-meter badge, out-of-stock states |
| **AuroraButton** | Animated gradient CTA button |

### 🔍 SEO & GEO Optimization

| Item | Implementation |
|---|---|
| **Technical SEO** | sitemap.xml, robots.txt, canonical tags, www→non-www 301 redirect |
| **Structured Data** | JSON-LD: Organization, CollectionPage, FAQPage, BreadcrumbList, Article |
| **E-E-A-T Signals** | About page 700+ words, founding date, team, mission, values |
| **AI Search (GEO)** | `/guide/buy-ppf` landing page targeting ChatGPT/Gemini citations |
| **llms.txt** | AI-readable site description for LLM crawlers |
| **IndexNow** | Bing fast-indexing protocol (HTTP 202 confirmed) |
| **Alt Text** | All product images with category-enriched alt attributes |
| **Security Headers** | HSTS, X-Frame-Options, X-Content-Type-Options, Referrer-Policy |
| **AI Crawlers** | GPTBot, Google-Extended, ClaudeBot — intentionally unblocked for GEO |

### 🔗 Integrations

| Integration | Status |
|---|---|
| **Torob Product Feed** | `/torob.xml` — 156 products in Google Base RSS format |
| **Enamad Trust Seal** | Iranian e-commerce trust badge |
| **WhatsApp & Phone CTA** | Direct call dropdown in header |
| **IndexNow / Bing** | Fast URL submission protocol |

### ⚙️ DevOps & Infrastructure

| Item | Details |
|---|---|
| **Server** | Ubuntu 22.04 VPS |
| **Process Manager** | PM2 with auto-restart on crash |
| **Reverse Proxy** | nginx with 3 server blocks (www redirect, HTTPS, HTTP→HTTPS) |
| **SSL** | Let's Encrypt via Certbot |
| **Database** | Neon serverless PostgreSQL |
| **Source Control** | GitHub — 100+ commits |

---

## 📂 Project Structure

```
src/
├── app/
│   ├── about/              E-E-A-T optimized — 700+ words
│   ├── guide/buy-ppf/      GEO landing page (AI search optimization)
│   ├── products/
│   │   ├── [id]/           Dynamic product detail (SSG, 150+ static routes)
│   │   ├── avery-dennison/ Category page + FAQPage schema
│   │   ├── kodak/
│   │   ├── solar/
│   │   └── installation-tools/
│   ├── cart/
│   ├── checkout/
│   ├── admin/              Protected by nginx Basic Auth
│   ├── api/orders/         REST API for order management
│   ├── robots.ts           Dynamic robots.txt with AI crawler rules
│   ├── sitemap.ts          Auto-generated XML sitemap
│   └── layout.tsx          Organization schema + OpenGraph global
├── components/
│   ├── ui/
│   │   ├── button.tsx              shadcn/ui Button (Radix + CVA)
│   │   ├── hover-glow-button.tsx   Custom animated glow buttons
│   │   └── circular-gallery.tsx    3D rotating gallery (GSAP)
│   ├── HotspotImageSelector.tsx    Click-zone product variant selector
│   ├── MeterSlider.tsx             Per-meter purchase slider
│   ├── ProductCard.tsx
│   ├── HeroSlider.tsx
│   └── ... 20+ more components
├── lib/
│   ├── products.ts         Single source of truth — 1,400+ lines
│   └── db.ts               Neon PostgreSQL client
└── context/
    └── CartContext.tsx     Global cart state with persistence
```

---

## 🎯 Technical Highlights

### Per-Meter PPF Purchasing
محصولات PPF متری با slider تعاملی — کاربر متراژ (۱ تا ۱۵ متر) رو انتخاب می‌کنه و قیمت real-time محاسبه می‌شه.

```tsx
// Real-time price calculation per meter
const pricePerMeter = pricePerRoll / rollMeters;
const currentPrice = Math.round(meters * pricePerMeter);
onSelectionChange(meters, currentPrice);
```

### HotspotImageSelector
کلیک روی ناحیه‌های مختلف یک تصویر کامپوزیت برای انتخاب variant محصول. Canvas crop برای نمایش تصویر بریده‌شده در سبد خرید.

```tsx
// Click zones mapped to product variants
hotspots: [
  { id: "russia-eagle", x: 22, y: 18, w: 24, h: 24 },
  { id: "dragon",       x: 52, y: 18, w: 24, h: 24 },
]
```

### GEO Optimization (AI Search)
صفحه اختصاصی با title دقیقاً برابر query کاربر در ChatGPT — برای کسب citation در AI search engines:

```
Title: "بهترین سایت ایرانی برای خرید PPF | راهنمای کامل خرید PPF در ایران"
+ Article JSON-LD schema
+ FAQPage schema
+ llms.txt for LLM crawler guidance
+ IndexNow submission to Bing
```

### nginx Security Headers
```nginx
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
proxy_hide_header X-Powered-By;
```

### Torob Product Feed
فید XML استاندارد برای ثبت در قیمت‌یاب ترب:
```
GET https://wrapmode.ir/torob.xml
→ 156 products
→ Google Base RSS format
→ Real-time prices from products data
→ utm_source=Torob tracking
```

---

## 📊 Numbers

| Metric | Value |
|---|---|
| Total Products | 150+ |
| Git Commits | 100+ |
| Source Files | 98 (TSX + TS) |
| Products Data | 1,400+ lines |
| Torob Feed Items | 156 |
| Category Pages | 6 (with FAQ + structured data) |
| Pages with JSON-LD | 10+ |
| Covered Provinces | 31 (سراسر ایران) |

---

## 🛠️ Tech Stack

```
Language        TypeScript 5
Framework       Next.js 16.2 (App Router, SSR/SSG)
Styling         Tailwind CSS v4
Animation       Framer Motion · GSAP
UI Primitives   Radix UI · class-variance-authority
Icons           Lucide React
Database        Neon PostgreSQL (pg driver)
Server          Ubuntu VPS · PM2 · nginx
SSL             Let's Encrypt / Certbot
```

---

## 👨‍💻 Developer

**محمد حاصلی — Mohammad Haseli**
طراح و توسعه‌دهنده وب

- 🌐 [wrapmode.ir](https://wrapmode.ir)
- [![LinkedIn](https://img.shields.io/badge/LinkedIn-Mohammad_Haseli-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohammad-hasseli-59a624362/)

---

> این پروژه نمونه‌کاری از طراحی و توسعه **full-stack** یک فروشگاه اینترنتی واقعی است —
> از صفر تا دیپلوی روی سرور واقعی، با بهینه‌سازی SEO کامل و GEO برای موتورهای جستجوی سنتی و هوش مصنوعی.

<div align="center">

**⭐ اگه این پروژه برات جالب بود، یه ستاره بده!**

</div>
