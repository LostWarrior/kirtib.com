---
date: 2026-04-01
title: Resume
linktitle: resume
url: /resume/
showthedate: false
---

Product engineer and former startup co-founder who owns problems end to end, from customer discovery and experiment design to distributed systems and high-scale database migrations. Over six years at GoCardless I have led growth products, run a cross-functional team, and now work on the reliability of core payment infrastructure. I care about why a system exists, who it serves, and whether it actually moved the needle.

***

#### <b> EXPERIENCE </b>

###### <b><span class="pink-color" style="color:#ff4088;">GoCardless, London</span> — Software Engineer</b> *<small>(Mar 2020 - Present)</small>*

**Distributed Systems, Scalability and Performance**
*   Co-designed the migration of GoCardless's core payments monolith (10M payments on peak days) from Postgres to YugabyteDB, so it can scale horizontally.
*   Made the migration pipeline for our 14 TB dataset 25x faster (600 hours down to 24) by reworking the schema, tuning the database, and digging into YugabyteDB Voyager's partition filtering and CDC replication issues.
*   Designed and shipped a Postgres function to replace direct `pg_locks` queries in our job system, unblocking 21 high-volume job classes for the YugabyteDB migration. Validated it against both databases, then rolled it out behind a feature flag (5% to 100%) with a latency probe watching production. Lock lookup went from ~100ms to ~3ms and P99 latency halved.
*   Led a cross-team E2E testing effort to catch edge cases in legacy services, built dry-run tooling with automated fallbacks, rehearsed the cutover repeatedly in production-parallel environments, and agreed readiness criteria with stakeholders for a zero-downtime switch.
*   Run Game Days to find gaps in our systems, write the runbooks the wider team uses, and onboard engineers inside and outside the team so no one person is a single point of failure.

**Product Engineering (Tech Lead)**
*   As tech lead for Digital Experience, led a team across product, engineering and marketing, acting as product owner, engineering lead and main point of contact for stakeholders. Set the technical direction for a marketing platform with 3M+ monthly visitors and mentored engineers.
*   Owned the merchant sign-up redesign end to end, across frontend and backend. More than half of merchants dropped out at the top of the funnel because we asked for too much upfront, so I cut the first step down to the essentials and A/B tested each change in Optimizely. Activation went up 22%.
*   Asking for less upfront meant catching spam another way, so I built email verification (schema, API, localised templates, SendGrid quality checks), pwned-password checks, rate limiting, reCAPTCHA and device-ID tracking, updated our spam-detection ML model, and passed spam signals downstream so fake accounts were blocked automatically. This removed a recurring source of incidents.
*   Scoped and planned the referral rewards system for international growth campaigns, including the technical approach, Optimizely experiments and lifecycle messaging through Braze, then handed it to the team to build with ongoing tech guidance.
*   Planned and led frontend delivery of the company-wide website rebrand, including scoping, prioritisation and stakeholder updates, and moved our content platform from Prismic to Contentful.
*   Built the monorepo template (TypeScript, Next.js, React, Lerna) that every new UI project starts from, shrank bundle sizes, raised test coverage to 95%, and contributed to Flux, our component library.
*   Cut build times from 60 to 15 minutes and infrastructure costs by 87%, and moved services from CircleCI to GitHub Actions, AWS to GCS, and Helm to our internal deploy tooling.
*   Connected GA, BigQuery and Looker so marketing could attribute results across channels.

###### <b><a href="https://kobitab.com" class="pink-color" style="color:#ff4088;">KobiTab</a> — Founder</b> *<small>(Feb 2026 - Present)</small>*
*   Built and launched a household brain for macOS that pulls a family's scattered files, calendars, emails and notes into one place and turns them into actionable tasks.
*   Designed it local-first: indexing and search run on-device with no account needed, and AI is optional, so users can bring their own provider or keep inference fully local.
*   Built review-before-run agents for everyday family admin like calendar drafting, nanny coordination and chores, plus plain-language answers with cited sources (e.g. shoe sizes, vaccine records).
*   Grown to 2,000 users organically through word of mouth, with no paid marketing.

###### <b><span class="pink-color" style="color:#ff4088;">Walmart Labs</span> — Software Engineer</b>
*   Developed the Fitment Widget for Walmart.com (React/Redux), a micro-frontend designed to handle high-concurrency traffic on product pages while verifying auto-part compatibility.
*   Spent brief time working on automating backend services for the registry, implementing caching strategies to ensure consistency across distributed nodes.

{{< details "See more" >}}

Built the fitment verification widget for Walmart.com auto parts using React, Redux, Electrode and Hapi.js - showing a 9% increase in Add-to-Cart metrics for the category.

<iframe width="100%" height="315" src="https://www.youtube.com/embed/BcpDr0CcIxA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen style="margin-top: 10px;"></iframe>

<div style="display: flex; gap: 10px; margin-top: 10px; flex-wrap: wrap;">
  <a href="/files/fitment.png" target="_blank"><img src="/files/fitment.png" width="200" alt="Fitment Widget"/></a>
  <a href="/files/fitment-full.png" target="_blank"><img src="/files/fitment-full.png" width="200" alt="Full View"/></a>
  <a href="/files/fitment-more-info.png" target="_blank"><img src="/files/fitment-more-info.png" width="200" alt="More Info"/></a>
</div>
{{< /details >}}

###### <b><span class="pink-color" style="color:#ff4088;">Radiolocus, Mumbai & Bangalore</span> — Software Engineer</b>
*   Led the frontend team at the intersection of engineering and product. This role came with a lot of autonomy and responsibility and included mentoring and leading the team. 

{{< details "See more" >}}
Some examples of work my team and I did using high-density urban datasets (e.g. VirginMedia, SmartCity India, European Airports) our focus was on rendering performance for datasets with millions of data points and high frequency updates. Helping our customers to make sense of the data and make informed decisions.

**VirginMedia Dashboard:**
{{< video src="/files/virginmedia.webm?rel=0" >}}

**SmartCity Dashboard:**
{{< video src="/files/smartcity.webm?rel=0" >}}
{{< /details >}}

###### <b><span class="pink-color" style="color:#ff4088;">Get Jugaad, India</span> — Co-founder</b>
*   Co-founded a ridesharing app and platform for high-density Indian cities while at university.
*   Owned customer discovery, product design, community building and go-to-market for new cities — talking to riders and drivers, turning interviews into product decisions, and iterating on what we learned.
*   Selected as India's official startup in Steve Blank's Lean Startup Initiative, earning the chance to pitch to investors in Silicon Valley.
*   We wound it down after hitting a regulatory wall: at the time, Indian law didn't allow charging for rides in privately registered vehicles.
*   [Archived site](https://web.archive.org/web/20130215083405/http://getjugaad.com:80/faq.php)

#### <b> PROJECTS </b>

*   **[knowledge-base](https://github.com/LostWarrior/knowledge-base):** A zero-dependency CLI for organizing project context in markdown. Designed for both human readability and efficient AI agent navigation, featuring automated indexing and lifecycle management.
*   **[wodehouse-gpt](https://github.com/LostWarrior/wodehouse-gpt):** A raw PyTorch, character-level GPT-style transformer built without pre-trained models or Hugging Face, trained on P.G. Wodehouse novels.
*   **[Calliope Canvas](https://github.com/LostWarrior/Calliope-Canvas):** A TypeScript/React framework for building code-driven, interactive technical presentations.
#### <b> EDUCATION </b>

###### <b> <span class="pink-color" style="color:#ff4088;">BRCM</span> — B.E. (Computer Science & Engineering) </b> *<small>Honors</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">TAKSHASHILA INSTITUTION</span> — GCPP </b> *<small>Graduated</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">NALSAR</span> — P.G. Diploma (International Humanitarian Law) </b> *<small>First Class</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">University of London</span> — Economics </b> *<small>Incomplete</small>*
