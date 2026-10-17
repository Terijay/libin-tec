# Libin Tec Website

Premium, responsive website for Libin Tec: **Logo Design**, **IoT Products** and **GST Registration & Filings**.

Built with Next.js (App Router), React, TypeScript, Tailwind CSS v4, Motion for React and Lucide icons.


## Pages

| Route | Page |
| --- | --- |
| `/` | Home |
| `/about` | About Us |
| `/logo-design` | Logo Design |
| `/iot-products` | IoT Products |
| `/gst-services` | GST Registration & Filings |
| `/contact` | Contact Us |

Plus a custom 404 page.

## Requirements

- Node.js 20.9 or newer
- npm

## Install and run

```bash
npm install
npm run dev        # http://localhost:3000
```

## Production build

```bash
npm run typecheck  # optional type check
npm run build
npm run start
```

## Replace the placeholder content

| What | Where |
| --- | --- |
| Company name, email, phone, WhatsApp, address, map, enquiry endpoint | `src/config/site.ts` (plain values) |
| Services text | `src/data/services.ts` |
| IoT product catalogue (currently **samples**) | `src/data/products.ts` |
| Logo portfolio (currently **samples**) | `src/data/portfolio.ts` |
| GST content and FAQs | `src/data/gst.ts` |
| Statistics (shown as `--` until you add real numbers) | `src/data/stats.ts` |
| Testimonials (section hidden until you add real ones) | `src/data/stats.ts` |
| Logo | `src/components/layout/Logo.tsx` |
| Colours | `src/app/globals.css` (`@theme` block) |

The About page mission, vision and values are generic draft text. Edit them to match your company, and add your real company story.

## Contact form

The form validates input and keeps submission logic in `src/lib/submitEnquiry.ts`.

- With an empty `enquiryEndpoint`, the form runs in **demo mode**. It clearly says nothing was sent and offers an email link instead.
- To go live, create an endpoint (for example a route handler at `src/app/api/enquiry/route.ts` that sends email through a provider) and set `enquiryEndpoint: "/api/enquiry"` in `src/config/site.ts`. Keep provider API keys in server-side environment variables (never in frontend code).

## Deploy

### GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<your-user>/<your-repo>.git
git push -u origin main
```

### Vercel

1. Sign in at vercel.com and choose **Add New > Project**.
2. Import your GitHub repository. Vercel detects Next.js automatically.
3. Click **Deploy**.

## Project structure

```
src/
  app/            routes, layouts, global styles
  components/
    layout/       Navbar, MobileMenu, Footer, Logo
    sections/     HeroSection, PageHero, StatsSection, TestimonialsSection
    ui/           Button, SectionHeading, ServiceCard, ProductCard, PortfolioCard, CTASection, FAQAccordion, FeatureCard, Counter
    motion/       AnimatedBackground, ScrollReveal, Providers (reduced-motion)
    forms/        ContactForm
    illustrations/ LogoMark, DeviceIllustration
  config/         site details and navigation
  data/           services, products, portfolio, GST, stats
  lib/            validation, submission, helpers
  types/          shared TypeScript types
```

## Notes

- Animations respect the visitor's reduced-motion setting (Motion `MotionConfig` plus a CSS media query).
- GST content is general information only and is not legal or tax advice.
- Fonts (Inter, Space Grotesk) load through `next/font/google` at build time.
