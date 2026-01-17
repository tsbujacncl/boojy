# Boojy - Tech Stack

## Overview

Solo project built by Tyr.

---

## Website (boojy.org)

| Component | Service |
|-----------|---------|
| Domain | Namecheap |
| Hosting | Netlify |
| Forms | Netlify Forms |
| Framework | Plain JavaScript |
| Version Control | GitHub |
| CI/CD | Netlify (auto-deploys from GitHub) |

---

## Analytics & Monitoring

| Component | Service |
|-----------|---------|
| Website Analytics | Umami (self-hosted) |
| Umami Hosting | Railway.com |
| Umami Database | Railway PostgreSQL |
| App Crash Reports | Sentry.io (opt-in) |

---

## Email & Communication

| Component | Service |
|-----------|---------|
| Newsletter Signup | Mailchimp |
| Contact Email | tyr@boojy.org |

---

## Boojy Audio App

| Component | Technology |
|-----------|------------|
| Framework | Flutter |
| Platforms (Current) | macOS, Windows |
| Platforms (Future) | iPad, Linux, Web |
| Download Hosting | GitHub Releases (recommended) |

---

## Data & Privacy

| Data Type | Storage |
|-----------|---------|
| User projects | Local only (user's computer) |
| Newsletter emails | Mailchimp |
| Form submissions | Netlify Forms |
| Crash reports | Sentry.io |
| Analytics | Umami (Railway) |

---

## Architecture Diagram

```
┌─────────────────────────────────────────────────────────────────────────┐
│                              USERS                                      │
└─────────────────────────────────────────────────────────────────────────┘
                                    │
                ┌───────────────────┼───────────────────┐
                │                   │                   │
                ▼                   ▼                   ▼
┌───────────────────────┐ ┌─────────────────┐ ┌─────────────────────────┐
│      boojy.org        │ │  Boojy Audio    │ │     tyr@boojy.org       │
│      (Website)        │ │     (App)       │ │       (Email)           │
│                       │ │                 │ │                         │
│  Hosting: Netlify     │ │ Framework:      │ │  Contact &              │
│  Forms: Netlify       │ │ Flutter         │ │  Support                │
│  JS: Plain            │ │                 │ │                         │
└───────────────────────┘ └─────────────────┘ └─────────────────────────┘
          │                       │
          │                       │
          ▼                       ▼
┌───────────────────────┐ ┌─────────────────┐
│       Umami           │ │    Sentry.io    │
│    (Analytics)        │ │ (Crash Reports) │
│                       │ │                 │
│  Hosting: Railway     │ │  Opt-in only    │
│  DB: Railway Postgres │ │                 │
└───────────────────────┘ └─────────────────┘
          
┌───────────────────────┐ ┌─────────────────┐
│      Mailchimp        │ │ GitHub Releases │
│    (Newsletter)       │ │  (Downloads)    │
│                       │ │                 │
│  Email signups        │ │  .dmg, .exe     │
│  Unsubscribe links    │ │  Versioned      │
└───────────────────────┘ └─────────────────┘
```

---

## Costs

| Service | Cost |
|---------|------|
| Namecheap (domain) | ~£10/year |
| Netlify | Free tier |
| Railway (Umami) | Free tier / ~$5/month |
| Sentry.io | Free tier |
| Mailchimp | Free tier (up to 500 contacts) |
| GitHub | Free |
| **Total** | ~£10/year + ~$0-5/month |

---

## Free Tier Limits

| Service | Free Limit |
|---------|------------|
| Netlify | 100GB bandwidth/month, 300 build mins |
| Railway | $5 credit/month |
| Sentry | 5K errors/month |
| Mailchimp | 500 contacts, 1K emails/month |
| GitHub Releases | 2GB per file |

---

## Future Considerations

| When | Consider |
|------|----------|
| 500+ newsletter subscribers | Upgrade Mailchimp or switch to Buttondown |
| High traffic | Add Cloudflare CDN (free) |
| Many crash reports | Upgrade Sentry |
| Large downloads | Consider Cloudflare R2 |