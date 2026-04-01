---
date: 2026-04-01
linktitle: resume
showthedate: false
---

### <b> <span class="dark-highlight" style="color:#555;">Kirti Bhardwaj</span> </b>

*Software engineer with experience across ecommerce, analytics, growth, and payments infrastructure. Currently focused on database scalability - migrating a 15TB payments database from PostgreSQL to YugabyteDB. Previously led frontend platform and growth engineering teams.*

***

#### <b> EXPERIENCE </b>

###### <b><span class="pink-color" style="color:#ff4088;">GoCardless, London</span> — Software Engineer</b> *<small>(Mar 2020 - Present)</small>*

**Database Migration & Infrastructure (2025 - Present)**

Part of the Payments Runway team focused on scalability - actively migrating GoCardless's core payments database from PostgreSQL to YugabyteDB (distributed SQL) with zero downtime. Phase 1 (~500GB) complete. Currently working on Phase 2 (~15TB).

>* Led the cutover of sandbox-staging to YugabyteDB across three attempts - debugging replication failures, stop-writes coordination, permission models, and partition handling. Wrote the cutover runbook used by the wider team
* Investigated a critical ~1000x slowdown in Voyager's data import - traced through three code paths to find recovery mode falling back to per-row COPY operations. Defined recovery procedures for the team
* Authored a database function (query_advisory_locks) to optimise advisory lock queries in the job processing system. Built latency probes with Prometheus histograms and rolled out observability across staging and production
* Built a load testing platform from scratch (Ruby + Playwright + Node.js) with Prometheus metrics, Web Vitals, and Kibana logging - deployed as Kubernetes cron jobs
* Supported Phase 1 migration of 50+ ActiveRecord models to a dual-write pattern (CutoverRecord), removing foreign key dependencies and building connection validation scripts
* Contributed to custom Voyager tooling - schema transformation, table exclusion, ownership safeguards, and an alternative schema import path
* Part of the team effort to fix 100+ test compatibility issues between PostgreSQL and YugabyteDB

**Product Growth / Spark Team (2023 - 2024)**

>* Built the email verification system end-to-end (frontend + backend) - database schema, API routes, i18n email templates, SendGrid quality scoring, pwned password checks, and rate limiting. Reduced fraudulent signups across the funnel
* Owned the signup frontend in the Next.js monorepo - optimised forms, reCAPTCHA, conversion tracking, and payer growth loop experiments
* Integrated SendGrid's email validation API for spam labeling at signup - email verdict scoring, background worker for quality checks on updates
* Contributed to the referral rewards system - Optimizely experiments, Braze email triggers, and audience segmentation

**Frontend Platform / DX Team (2020 - 2022)** - Tech Lead, Digital Experience

Tech lead for the digital experience team, sitting at the cusp of product, management and tech. Managed stakeholder relationships, set technical direction for the team, and created the conditions for engineers to do their best work.

>* Owned the content platform powering GoCardless's public website - React with Prismic/Contentful CMS, multi-region support (EN/FR/ES/DE), and Terraform-managed routing
* Built the GA BigQuery analytics pipeline from scratch - GCP projects, IAM, service accounts, Firebase linking, and staging/production environments
* Built UI components in the shared React library (flux) and set up testing infrastructure in the frontend monorepo (ui-hub)

###### <b><span class="pink-color" style="color:#ff4088;">Walmart Labs</span> — Software Engineer III</b> *<small>(Jan 2019 - Sept 2019)</small>*

>* Built the fitment verification widget for Walmart.com auto parts using React, Redux, Electrode and Hapi.js - increased Add-to-Cart metrics for the category
* Automated baby Registry backend with cache implementation and cloud configuration management

###### <b><span class="pink-color" style="color:#ff4088;">Radiolocus, Mumbai and Bangalore</span> — Frontend Developer</b> *<small>(May 2015 - Sept 2018)</small>*

Led the frontend team at the intersection of engineering and product. Built D3-based analytics dashboards for clients including VirginMedia and the Government of India's SmartCity project. Handled data visualizations, code splitting, custom utilities, PHP authentication layer, and client-based customizations.

#### <b> PROJECTS </b>

###### <b> <span class="pink-color" style="color:#ff4088;">Get Jugaad</span> — Co-founder</b> *<small>(during university)</small>*

Ridesharing platform for India, built through Steve Blank's Lean Startup Initiative. Selected as the official Indian startup to pitch to investors in Silicon Valley.

#### <b> EDUCATION </b>

*Took the scenic route through engineering, international law, and economics. The common thread? I like understanding how complex systems work - then building them.*

###### <b> <span class="pink-color" style="color:#ff4088;">TAKSHASHILA INSTITUTION</span> — GCPP </b> *<small>Graduated</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">University Of London</span> — (ECONOMICS) </b> *<small>Incomplete</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">NALSAR</span> — P.G.Diploma (IHL) </b> *<small>First Class</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">BRCM</span> — B.E. (Computer Science And Engineering) </b> *<small>Honors</small>*
