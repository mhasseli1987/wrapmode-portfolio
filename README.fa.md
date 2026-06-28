<div align="center">

# 🚗 رپ‌مود — پلتفرم فروشگاهی آنلاین

**سایت زنده:** [wrapmode.ir](https://wrapmode.ir) &nbsp;|&nbsp; **توسعه‌دهنده:** محمد حاصلی

[![Next.js](https://img.shields.io/badge/Next.js-16.2-black?style=for-the-badge&logo=next.js)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6?style=for-the-badge&logo=typescript&logoColor=white)](https://typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-4169E1?style=for-the-badge&logo=postgresql&logoColor=white)](https://neon.tech)
[![Ubuntu VPS](https://img.shields.io/badge/Ubuntu-VPS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white)](https://ubuntu.com)

[🇬🇧 English version](./README.md)

</div>

---

## پروژه چیست؟

**رپ‌مود** یک فروشگاه آنلاین تخصصی برای فروش **PPF (فیلم محافظ بدنه خودرو)**، **کاور رنگی**، **شیشه دودی** و **ابزار نصب** است. این سایت به عنوان نماینده رسمی برندهای **Avery Dennison** و **KODAK** در ایران فعالیت می‌کند.

این پروژه از **صفر** طراحی، کدنویسی، دیپلوی و بهینه‌سازی شده — توسط یک نفر.

---

## معماری کلی

```
wrapmode.ir
├── فرانت‌اند      Next.js 16 App Router (SSR + SSG)
├── دیتابیس        Neon PostgreSQL (serverless)
├── احراز هویت     nginx Basic Auth (پنل ادمین)
├── سرور           Ubuntu VPS + PM2 + nginx
├── SSL            Let's Encrypt (Certbot)
└── DNS            Cloudflare
```

---

## قابلیت‌های پیاده‌سازی‌شده

### فروشگاه

| قابلیت | توضیح |
|---|---|
| **کاتالوگ محصول** | بیش از ۱۵۰ محصول در ۶ دسته‌بندی |
| **سبد خرید** | با Context API و ذخیره‌سازی مداوم |
| **فرآیند خرید** | چند مرحله‌ای با آدرس و ارسال |
| **مدیریت سفارش** | چرخه کامل سفارش (در انتظار → تأیید → ارسال) |
| **پنل ادمین** | داشبورد امن برای سفارشات، محصولات و تنظیمات |
| **خرید متری** | slider تعاملی برای خرید PPF به متر (۱ تا ۱۵ متر) |

### کامپوننت‌های اختصاصی UI

| کامپوننت | توضیح |
|---|---|
| **HoverGlowButton** | دکمه‌های متحرک با افکت glow — ۵ variant (aurora, pulse, neon, gradient, classic) |
| **HotspotImageSelector** | انتخاب variant محصول با کلیک روی نواحی تصویر کامپوزیت |
| **MeterSlider** | slider تعاملی با محاسبه قیمت real-time |
| **CircularGallery** | گالری ۳بعدی چرخان (با GSAP) |
| **HeroSlider** | اسلایدر خودکار با توقف هنگام hover |
| **ProductCard** | کارت محصول ریسپانسیو با حالت‌های ناموجود و خرید متری |
| **AuroraButton** | دکمه CTA با گرادیانت متحرک |

### سئو و بهینه‌سازی

| آیتم | پیاده‌سازی |
|---|---|
| **سئو تکنیکال** | sitemap.xml، robots.txt، canonical، ریدایرکت ۳۰۱ www به non-www |
| **داده ساختاریافته** | JSON-LD: Organization، CollectionPage، FAQPage، BreadcrumbList، Article |
| **E-E-A-T** | صفحه درباره ما ۷۰۰+ کلمه، تاریخ تأسیس، تیم، مأموریت |
| **GEO (جستجوی هوش مصنوعی)** | صفحه `/guide/buy-ppf` برای citation در ChatGPT/Gemini |
| **llms.txt** | راهنمای متنی برای AI crawlerها |
| **IndexNow** | پروتکل ثبت سریع URL در Bing (HTTP 202 تأیید شد) |
| **Alt Text** | همه تصاویر محصول با alt غنی‌شده با کلیدواژه دسته‌بندی |
| **هدرهای امنیتی** | HSTS، X-Frame-Options، X-Content-Type-Options، Referrer-Policy |

### یکپارچه‌سازی‌ها

| یکپارچه‌سازی | وضعیت |
|---|---|
| **فید ترب** | `/torob.xml` — ۱۵۶ محصول در فرمت Google Base RSS |
| **اینماد** | نماد اعتماد الکترونیک وزارت صمت |
| **واتساپ و تماس مستقیم** | dropdown تماس در هدر |
| **IndexNow / Bing** | پروتکل ثبت سریع URL |

### زیرساخت و DevOps

| آیتم | جزئیات |
|---|---|
| **سرور** | Ubuntu 22.04 VPS |
| **مدیریت پروسس** | PM2 با auto-restart |
| **ریورس پروکسی** | nginx با ۳ server block |
| **SSL** | Let's Encrypt via Certbot |
| **دیتابیس** | Neon PostgreSQL (serverless) |
| **کنترل نسخه** | GitHub — بیش از ۱۰۰ commit |

---

## ساختار پروژه

```
src/
├── app/
│   ├── about/                 صفحه درباره ما — بهینه‌شده برای E-E-A-T
│   ├── guide/buy-ppf/         لندینگ پیج GEO برای جستجوی هوش مصنوعی
│   ├── products/
│   │   ├── [id]/              صفحه محصول داینامیک (SSG، ۱۵۰+ route)
│   │   ├── avery-dennison/    صفحه دسته‌بندی + FAQPage schema
│   │   ├── kodak/
│   │   ├── solar/
│   │   └── installation-tools/
│   ├── cart/
│   ├── checkout/
│   ├── admin/                 محافظت‌شده با nginx Basic Auth
│   ├── api/orders/            REST API مدیریت سفارش
│   ├── robots.ts              robots.txt داینامیک با قوانین AI crawler
│   ├── sitemap.ts             sitemap.xml خودکار
│   └── layout.tsx             Organization schema + OpenGraph سراسری
├── components/
│   ├── ui/
│   │   ├── button.tsx              دکمه shadcn/ui (Radix + CVA)
│   │   ├── hover-glow-button.tsx   دکمه‌های glow متحرک
│   │   └── circular-gallery.tsx    گالری ۳بعدی (GSAP)
│   ├── HotspotImageSelector.tsx    انتخاب variant با کلیک روی تصویر
│   ├── MeterSlider.tsx             slider خرید متری
│   ├── ProductCard.tsx
│   ├── HeroSlider.tsx
│   └── ... بیش از ۲۰ کامپوننت دیگر
├── lib/
│   ├── products.ts             منبع اصلی داده — بیش از ۱۴۰۰ خط
│   └── db.ts                   کلاینت Neon PostgreSQL
└── context/
    └── CartContext.tsx          وضعیت سبد خرید با ذخیره‌سازی مداوم
```

---

## نکات تکنیکال برجسته

### خرید PPF به متر
کاربر با slider متراژ دلخواه (۱ تا ۱۵ متر) رو انتخاب می‌کنه و قیمت لحظه‌ای محاسبه می‌شه:

```tsx
const pricePerMeter = pricePerRoll / rollMeters;
const currentPrice = Math.round(meters * pricePerMeter);
onSelectionChange(meters, currentPrice);
```

### HotspotImageSelector
کلیک روی نواحی مختلف یک تصویر کامپوزیت برای انتخاب variant — با Canvas crop برای نمایش بریده‌شده در سبد خرید:

```tsx
hotspots: [
  { id: "russia-eagle", x: 22, y: 18, w: 24, h: 24 },
  { id: "dragon",       x: 52, y: 18, w: 24, h: 24 },
]
```

### بهینه‌سازی GEO (جستجوی هوش مصنوعی)
صفحه اختصاصی با title دقیقاً برابر query کاربر در ChatGPT:

```
عنوان: "بهترین سایت ایرانی برای خرید PPF | راهنمای کامل خرید PPF در ایران"
+ Article + FAQPage schema
+ llms.txt برای راهنمایی AI crawlerها
+ ثبت URL در Bing با IndexNow
```

### هدرهای امنیتی nginx

```nginx
add_header Strict-Transport-Security "max-age=31536000; includeSubDomains" always;
add_header X-Frame-Options "SAMEORIGIN" always;
add_header X-Content-Type-Options "nosniff" always;
add_header Referrer-Policy "strict-origin-when-cross-origin" always;
proxy_hide_header X-Powered-By;
```

---

## آمار پروژه

| متریک | مقدار |
|---|---|
| تعداد محصولات | بیش از ۱۵۰ |
| تعداد commit | بیش از ۱۰۰ |
| فایل‌های سورس | ۹۸ فایل (TSX + TS) |
| خطوط داده محصول | بیش از ۱۴۰۰ |
| آیتم‌های فید ترب | ۱۵۶ |
| صفحات دسته‌بندی | ۶ (با FAQ + داده ساختاریافته) |
| صفحات با JSON-LD | بیش از ۱۰ |
| استان‌های تحت پوشش | ۳۱ |

---

## تکنولوژی‌های استفاده‌شده

```
زبان برنامه‌نویسی    TypeScript 5
فریم‌ورک            Next.js 16.2 (App Router، SSR/SSG)
استایل              Tailwind CSS v4
انیمیشن            Framer Motion · GSAP
UI Primitives       Radix UI · class-variance-authority
آیکون              Lucide React
دیتابیس            Neon PostgreSQL (درایور pg)
سرور               Ubuntu VPS · PM2 · nginx
SSL                Let's Encrypt / Certbot
```

---

## توسعه‌دهنده

**محمد حاصلی — Mohammad Haseli**
طراح و توسعه‌دهنده وب

- 🌐 [wrapmode.ir](https://wrapmode.ir)
- [![LinkedIn](https://img.shields.io/badge/LinkedIn-Mohammad_Haseli-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mohammad-hasseli-59a624362/)

---

> این پروژه نمونه‌کاری از طراحی و توسعه **full-stack** یک فروشگاه اینترنتی واقعی است —
> از صفر تا دیپلوی روی سرور، با بهینه‌سازی SEO کامل و GEO برای موتورهای جستجوی سنتی و هوش مصنوعی.

<div align="center">

**⭐ اگه این پروژه برات جالب بود، یه ستاره بده!**

</div>
