# CustomPath Learning

**Full-stack tutoring platform connecting students with certified teachers for personalized 1-on-1 sessions.**

🌐 **Live site:** [custompathlearning.com](https://custompathlearning.com)
👩‍💻 **Built by:** Leanne Byrne · Co-Founder & Technology Lead
📍 **Status:** Live in production

---

## About the Project

CustomPath Learning is a startup I co-founded to connect families with certified teachers for personalized tutoring. I own the entire technical side of the business — architecture, backend, frontend, deployment, payments, database, and ongoing operations.

This is not a class project or a tutorial. It is a **live, production platform** processing real payments through Stripe, storing real user data, and operating as a functioning business with active tutors and families.

---

## What I Built

### End-to-end platform
- **Public marketing site** — hero, paths, feature sections, information request form
- **Student dashboard** — booking, session history, learning plan, session notes
- **Tutor dashboard** — availability calendar, schedule, session notes, earnings
- **Admin dashboard** — full oversight of bookings, tutors, students, payments, and orientations

### Core systems
- **Authentication** — stateless JWT auth with role-based access control (student / tutor / admin)
- **Booking engine** — tutor directory, availability calendar, session booking with conflict prevention
- **Payment processing** — Stripe checkout integration with webhook handling for booking confirmations
- **Email automation** — transactional emails via SendGrid for bookings, orientations, and handbook signatures
- **Legal compliance** — electronic handbook signature flow with PDF generation and archival
- **Admin controls** — learning plan editor, tutor qualifications, payment tracking, orientation management

---

## Tech Stack

| Layer | Technology |
|-------|------------|
| **Language** | Java 21 |
| **Backend framework** | Spring Boot 3 |
| **Database** | PostgreSQL (Supabase) |
| **ORM** | Hibernate / JPA |
| **Authentication** | JWT (stateless, custom implementation) |
| **Payments** | Stripe API + Webhooks |
| **PDF generation** | OpenPDF |
| **Email** | SendGrid |
| **Frontend** | Vanilla JavaScript SPA (single-file architecture, no framework overhead) |
| **Deployment** | Railway (production) with continuous deployment from GitHub |
| **DNS / SSL / CDN** | Cloudflare |
| **Build tool** | Maven |
| **Version control** | Git / GitHub |

---

## Architecture

```
                   custompathlearning.com
                    (Cloudflare DNS + SSL)
                             │
                             ▼
                ┌─────────────────────────────┐
                │   Single-Page Application   │
                │   (Served by Spring Boot)   │
                └─────────────────────────────┘
                             │
                             │  REST API (JSON)
                             ▼
                ┌─────────────────────────────┐
                │   Spring Boot 3 (Java 21)   │
                │         on Railway          │
                │                             │
                │   ├─ JWT Auth Filter        │
                │   ├─ Auth Controller        │
                │   ├─ Bookings Controller    │
                │   ├─ Tutor Profiles         │
                │   ├─ Availability           │
                │   ├─ Session Notes          │
                │   ├─ Orientations           │
                │   ├─ Stripe Checkout        │
                │   ├─ Stripe Webhooks        │
                │   ├─ Handbook Signatures    │
                │   ├─ PDF Service            │
                │   └─ Email Service          │
                └─────────────────────────────┘
                             │
                             ▼
                ┌─────────────────────────────┐
                │  PostgreSQL (Supabase)      │
                │                             │
                │  profiles, bookings,        │
                │  tutor_profiles,            │
                │  availability_slots,        │
                │  session_notes,             │
                │  orientation_requests,      │
                │  handbook_signatures        │
                └─────────────────────────────┘

     External integrations:
     ├─ Stripe (payments + webhook callbacks)
     └─ SendGrid (transactional email + PDF attachments)
```

---

## Features Worth Highlighting

### 🔐 Secure signed-document workflow
When a family books their first session, they sign the Parent & Student Handbook electronically. The system:
1. Captures their typed signature, IP address, and timestamp
2. Generates a professionally formatted PDF of the complete signed agreement
3. Emails the PDF to the parent and both admins as a permanent legal record
4. Stores the signature in the database with version tracking for future handbook updates

### 💳 End-to-end Stripe payment flow
- Checkout session created on booking request with student and session metadata
- User redirected to Stripe-hosted checkout (PCI compliance handled by Stripe)
- Webhook endpoint verifies Stripe signatures and confirms bookings server-side
- Graceful handling of payment failures and cancellations

### 📅 Calendar-based availability system
Tutors set recurring or one-off availability slots. Students see only open slots in a mini-calendar that syncs live with the tutor's schedule — booked slots immediately disappear from the public view.

### 📝 Structured session notes
After each session, tutors log what was covered, student progress, next steps, and engagement rating. Parents and admins see a complete running record of every session.

### ⚙️ Full admin oversight
The admin dashboard provides a live view of every booking, tutor, student, session note, and payment due — with the ability to assign tutors, edit learning plans, track tutor qualifications by subject and grade level, and mark tutor payments as completed.

---

## My Role

**Technology & Operations Lead**

I am personally responsible for:

- Full backend architecture and API design
- Database schema design and data modeling
- JWT authentication and authorization logic
- Stripe integration (checkout sessions, webhooks, error handling)
- Email templates and SendGrid integration
- PDF generation for legal documents
- Frontend SPA (single-file HTML/CSS/JS, ~130KB)
- Production deployment to Railway with continuous delivery
- Cloudflare DNS, SSL, and CDN configuration
- Ongoing bug fixes, features, and operational support


---

## What I Learned

Building a real business platform taught me things no class could:

- **Production incidents are different from bugs on your laptop.** When a payment fails or an email doesn't send for a paying family, you fix it now and learn the hard way why resilience matters.
- **Database decisions matter.** I learned firsthand the tradeoff between `varchar(255)` and `text` columns when a learning plan overflowed.
- **Security is not optional.** Spring Security filter chains, CORS configuration, and JWT validation are not abstract concepts — they are the difference between a working app and an exposed one.
- **Users don't care about your code.** They care about whether the site loads, the button does the thing, and the email arrives. Ship often, test the full flow, and prioritize the user experience.

---

## Source Code Access

The production source code is maintained in a **private repository** for security reasons.

If you are a recruiter, hiring manager, or technical reviewer interested in seeing the code, I am happy to provide read-only access on request. Please reach out via email.

---

## Contact

**Leanne Byrne**
📧 [Contact via CustomPath Learning](https://custompathlearning.com)
🌐 [custompathlearning.com](https://custompathlearning.com)
💼 [LinkedIn](https://linkedin.com)

---

*CustomPath Learning is a live business, not a side project. Handle with curiosity and respect.*
