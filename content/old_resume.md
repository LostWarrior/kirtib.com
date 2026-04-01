---
date: 2026-04-01
draft: true
title: Old Resume
linktitle: resume
showthedate: false
---

Download <i class="fa fa-download"></i> [pdf](/files/resume.pdf) here
<!-- 
> 
* London, United Kingdom
* [Email](mailto:kirti.sbhardwaj@gmail.com) -->


### <b> <span class="dark-highlight" style="color:#555;">Kirti Bhardwaj</span> </b>

***

#### <b> SKILLS</b>

Ruby, Rails, TypeScript, JavaScript, SQL, PostgreSQL, React, Next.js, Terraform, GCP, Kubernetes, Docker, Prometheus, Playwright, GitHub Actions, Git

#### <b> EXPERIENCE </b>

###### <b><span class="pink-color" style="color:#ff4088;">GoCardless, London</span> — Software Engineer</b> *<small>(2020 - Present)</small>*

Payments infrastructure company processing $35B+ annually. Progressed from frontend platform work to a critical database migration across the core payments service.

**Database Migration & Infrastructure (2025 - Present)**

Part of the Payments Runway team focused on scalability - actively migrating GoCardless's core payments database from PostgreSQL to YugabyteDB (distributed SQL) with zero downtime. Phase 1 (~500GB) complete. Currently working on Phase 2 (~15TB).

>* Led the cutover of sandbox-staging to YugabyteDB across three attempts - debugging replication failures, stop-writes coordination, permission models, and partition handling. Wrote the definitive cutover runbook documenting lessons, fallback procedures, and pre-cutover checklists used by the wider team
* Contributed to the team's custom migration tooling around YugabyteDB Voyager - added methods for schema transformation, table exclusion, ownership safeguards, and an alternative schema import path to work around Voyager's silent failure modes
* Investigated and documented a critical ~1000x slowdown in Voyager's data import when restarting with `--on-primary-key-conflict IGNORE` - traced through three code paths to identify that recovery mode falls back to per-row COPY operations, and defined recovery procedures for the team
* Supported the team in Phase 1 migration of 50+ ActiveRecord models to a dual-write pattern (CutoverRecord), removing blocking foreign key dependencies and building connection validation scripts
* Authored a custom database function (query_advisory_locks) to optimise advisory lock queries in the job processing system, built latency probes with Prometheus histograms, and rolled out observability across staging and production
* Built a load testing platform from scratch (Ruby + Playwright + Node.js) with Prometheus metrics, Web Vitals collection, and Kibana logging - deployed as Kubernetes cron jobs to validate dashboard performance during migration
* Part of the team effort to fix 100+ test compatibility issues between PostgreSQL and YugabyteDB - non-deterministic ordering, DDL transaction differences, serialization errors, and partition lifecycle handling

**Product Growth / Spark Team (2023 - 2024)**

>* **S:** Fraudulent and low-quality signups were increasing operational costs with no way to verify merchant email addresses before onboarding. **T:** Build an email verification system from scratch. **A:** Designed and implemented end-to-end across frontend (Next.js) and backend (Rails) - database schema, API routes, i18n email templates, SendGrid email quality scoring, pwned password checks, and rate limiting. **R:** Deployed to production, reducing fraudulent signups and improving merchant quality across the funnel.
>
>* **S:** The signup form was a monolithic page with poor conversion and no experimentation capability. **T:** Own the signup frontend and enable rapid growth iteration. **A:** Took ownership of the signup flow in the Next.js monorepo, built optimised forms, integrated reCAPTCHA, added conversion tracking, and implemented payer growth loop experiments. **R:** Enabled the growth team to run A/B experiments on the signup funnel, improving conversion metrics.
>
>* **S:** No automated way to detect spam or low-quality email addresses at the point of signup. **T:** Add email quality scoring to the registration pipeline. **A:** Integrated SendGrid's email validation API, added email verdict and score fields to the user model, and built a background worker to check email quality on updates. **R:** Spam labeling enabled at signup, giving downstream teams a signal to filter low-quality accounts.
>
>* Contributed to the referral rewards system - helped build Optimizely experiment integration, Braze email triggers, and audience segmentation for merchant acquisition campaigns.

**Frontend Platform / DX Team (2020 - 2022)** - Tech Lead, Digital Experience

Tech lead for the digital experience team, sitting at the cusp of product, management and tech.

>* **S:** GoCardless's public website needed to support marketing content across multiple regions and languages, managed by non-technical teams. **T:** Build and maintain the content platform serving all public-facing pages. **A:** Became a core contributor (#6 overall) to the React application backed by Prismic and later Contentful CMS, with Terraform-managed routing for legal, pricing, partner, and FAQ pages across EN/FR/ES/DE regions. **R:** Marketing teams could independently publish and localise content across four regions without engineering involvement.
>
>* **S:** The marketing team had no analytics pipeline connecting Google Analytics data to BigQuery for cross-channel analysis. **T:** Set up the infrastructure to stream GA data into BigQuery. **A:** Built the entire pipeline from scratch - GCP projects, IAM roles, service accounts, Firebase linking, datasets, and staging/production environments integrated with the Utopia infrastructure platform. **R:** Marketing analytics team gained self-serve access to GA data in BigQuery, enabling cross-channel reporting.
>
>* **S:** Frontend teams lacked shared UI components and consistent testing across projects. **T:** Establish reusable component and testing infrastructure. **A:** Built UI components in the shared React library (flux) and set up jest-config and testing infrastructure in the frontend monorepo (ui-hub). **R:** Consistent UI patterns and test setup across frontend projects, reducing duplication and onboarding time.

###### <b><span class="pink-color" style="color:#ff4088;">Walmart Labs</span> — Software Engineer III</b> *<small>(Jan 2019 - Sept 2019)</small>*
Used react, redux, electrode and hapi.js to build the fitment widget for Walmart.com raising the ATC for auto parts by a significant number.
Played an integral role in getting the widget to work on product pages and helped other developers to be an effective part of the team. 
More about Fitment:

<iframe width="560" height="315" src="https://www.youtube.com/embed/BcpDr0CcIxA" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Helped automate the baby Registry backend for the Walmart.com including cache implementation and integrating with cloud configuration management. 

<a href="/files/fitment.png" target="_blank">
	<img src="/files/fitment.png" width="200" height="200" alt="fitment widget on product page" />
</a>
<a href="/files/fitment-full.png" target="_blank">
	<img src="/files/fitment-full.png" width="200" height="200" alt="fitment widget on product page" />
</a>
<a href="/files/fitment-more-info.png" target="_blank">
	<img src="/files/fitment-more-info.png" width="200" height="200" alt="fitment widget on product page"/>
</a>

###### <b><span class="pink-color" style="color:#ff4088;">Radiolocus, Mumbai and Bangalore</span> — Frontend Developer</b> *<small>(May 2015 - Sept 2018)</small>*
<b>Lead frontend team</b> while playing a role at intersection of engineering and
product. Gained experience in customer centric approach to solving issues
related to <b>navigation, user path, data analytics</b> and telling a story through
data so as to enable users to make informed decisions.
Built multiple dashboards and utilities with features such as:

>* D3 based visualizations
* Code splitting
* Custom Datepicker utilities, Graphs etc.
* Custom export utilities
* Client Based Customizations
* Complete php layer for authentication, jwt, session management
* Logging functionality etc.


*Earlier roles (2013-2014): Web Engineer at EatAds, Developer at Twyst, Senior Web Developer at GetFitGo, Tech Consultant at SocialProma - frontend development and dashboards across early-stage startups.*


#### <b> PROJECTS </b>

###### <b> <span class="pink-color" style="color:#ff4088;">Get Jugaad</span> </b> 

As a part of Lean Startup Initiative by Steve Blank worked on a ridesharing app and platform targeting customers in India. Team was selected as official startup from India giving us an opportunity to pitch to investors in Silicon Valley. Major responsibilities included:

>* Community Building
* Customer Onboarding and New Customer Acquisition

###### <b> <span class="pink-color" style="color:#ff4088;">VirginMedia Dashboard</span> </b> 

As a part of team at RadioLocus worked on dashboard for a city based analytics.

<video width="100%" height="400px" controls>
	<source src="/files/virginmedia.webm?rel=0" type="video/webm">
</video>

###### <b><span class="pink-color" style="color:#ff4088;"> SmartCity Dashboard </span></b> 

As a part of team at RadioLocus worked on dashboard for smartcity project by Governement Of India.

<video width="100%" height="400px" controls>
	<source src="/files/smartcity.webm?rel=0" type="video/webm">
</video>

#### <b> EDUCATION </b>

*Took the scenic route through engineering, international law, and economics. The common thread? I like understanding how complex systems work - then building them.*

###### <b> <span class="pink-color" style="color:#ff4088;">TAKSHASHILA INSTITUTION</span> — GCPP </b> *<small>Graduated</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">University Of London</span> — (ECONOMICS) </b> *<small>Incomplete</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">NALSAR</span> — P.G.Diploma (IHL) </b> *<small>First Class</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">BRCM</span> — B.E. (Computer Science And Engineering) </b> *<small>Honors</small>*
