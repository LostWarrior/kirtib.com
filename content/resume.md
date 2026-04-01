---
date: 2026-04-01
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

Payments infrastructure company processing $35B+ annually. Progressed from frontend platform work to leading a critical database migration across the core payments service.

**Database Migration & Infrastructure (2025 - Present)**

>* Leading migration of core payments database from PostgreSQL to YugabyteDB (distributed SQL) - migrating 50+ ActiveRecord models with dual-write patterns for zero-downtime cutover
* Built a load testing platform from scratch (Ruby + Playwright + Node.js) with Prometheus metrics, Web Vitals collection, and Kibana logging - deployed via Kubernetes cron jobs
* Authored database functions to optimise advisory lock queries, built latency probes with Prometheus histograms, and rolled out observability across staging and production
* Developed migration tooling around YugabyteDB Voyager - schema import, table exclusion logic, ownership safeguards, and connection validation for phased migration
* Fixed 100+ distributed database compatibility issues in the test suite - non-deterministic ordering, DDL transaction differences, serialization errors, and cross-database connections
* Managed infrastructure (Terraform/GCP) for cutover environments - database configs, connection pools, consoles, replica scaling, and disk provisioning

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

>* Core contributor (#6) to the content platform powering GoCardless's public website - React with Prismic/Contentful CMS, multi-region support (EN/FR/ES/DE), and Terraform-managed routing
* Set up Google Analytics BigQuery infrastructure from scratch - GCP projects, IAM roles, service accounts, Firebase linking, and dataset configuration
* Built UI components in the shared React component library and established testing infrastructure in the frontend monorepo

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


###### <b> <span class="pink-color" style="color:#ff4088;">EatAds, New Delhi </span> — Web Engineer </b> *<small>(Nov 2014 - Apr 2015)</small>*
Worked with a small team of six engineers to build a web and mobile app for
outdoor media:

>* Web platform for updating the project/campaign data
* Dashboard for advertisers to check the progress of campaigns and on different campaign sites
* Image manipulation
* Web app and mobile app integration.


###### <b><span class="pink-color" style="color:#ff4088;"> Twyst, Gurgaon </span> — Developer </b> *<small>(Jul 2014 - Nov 2014)</small>*

Worked with a small team of four developers to build the web platform of the hyperlocal startup Twyst:

>* Web Platform for Merchants to log in and see their data.
* Platform for users to discover the places to eat
* Reward system for each consecutive visit


###### <b> <span class="pink-color" style="color:#ff4088;">GetFitGo, Mumbai</span> — Senior Web Developer </b> *<small>(Apr 2014 - Jun 2014)</small>*
Worked with a team of three engineers to develop a social network for fitness enthusiasts with features such as

>* Suggested Friends
* Leadership Board and Community Boards
* Closed Groups/Community
* Automated Sync with devices like fitbit.
* Utility for installing and updating devices from windows and mac.


###### <b> <span class="pink-color" style="color:#ff4088;">SocialProma, Bangalore</span> — Tech Consultant, Developer and Writer </b> *<small>(Sep 2013 - Apr 2014)</small>*
Joined as an intern and later came on board as developer and tech consultant. Major responsibilities included:

>* Writing Tech Blogs and News
* Developing and designing website and creating wordpress plugins
* Speed optimization


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

###### <b> <span class="pink-color" style="color:#ff4088;">TAKSHASHILA INSTITUTION</span> — GCPP </b> *<small>Graduated</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">University Of London</span> — (ECONOMICS) </b> *<small>Incomplete</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">NALSAR</span> — P.G.Diploma (IHL) </b> *<small>First Class</small>*
###### <b> <span class="pink-color" style="color:#ff4088;">BRCM</span> — B.E. (Computer Science And Engineering) </b> *<small>Honors</small>*
