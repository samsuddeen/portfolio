# SEO-TASKS.md (V3: only pending work; completed steps removed)

## GLOBAL RULES (apply to every step)
- NEVER run `git push`, `git pull`, `git merge` into master, never deploy, never publish. LOCAL commits only.
- Work ONLY on branch `seo-fix`. Before every step run `git branch --show-current`. If it is not `seo-fix`, STOP and tell me.
- Never use `git add -A` or `git add .`. Stage only the specific files you edited.
- Do NOT touch, commit, delete or rename `assets/shamsudin-resume.pdf` or `assets/shamsudin-resume_old.pdf` (I manage the PDFs myself).
- Work on ONE step at a time. After finishing a step: tick its checkbox in PROGRESS, make a local commit, print a short changelog, then STOP and wait for me. Do not start the next step.
- Before starting a step: run `git status` and `git log --oneline -10`, and check what is already done so you only finish what is missing.
- The site must look IDENTICAL to the original at `origin/master` (except where a step changes text content). Do not change design, colors, spacing, fonts, layout, CSS class names/IDs, animations or functionality unless a step says so. Use `git show origin/master:<file>` to compare when unsure.
- Do not invent facts, numbers, links, clients, addresses or images. Use `<!-- TODO -->` for missing info.
- Keep all existing .html URLs working (no clean URLs).
- Never add outbound links to auditsystemshangrilabank.com or audit.trilokyasoft.com (private bank system). Show that project as text only.
- If something is not in this file or you are unsure, ask me instead of guessing.

## PROJECT FACTS
- Site: https://shamsudinaalam.com.np (NON-www is canonical). Static HTML/CSS/JS on GitHub Pages behind Cloudflare.
- Pages: index.html, about.html, projects.html, resume.html, services.html
- Owner: Shamsudin Aalam (also spelled Samsudin Alam)
- Main role: **Software Developer** (specialty: Laravel & PHP). 3+ years experience. Currently learning Python and Django.
- Location: **Kathmandu, Nepal** (public pages say only this; no street address)
- Phone: +977-9816266897 (tel: link) | Email: shamsudinaalam@gmail.com (mailto: link)
- Geo: geo.region NP-BA, geo.placename Kathmandu, geo.position 27.7172;85.3240, ICBM 27.7172, 85.3240
- JSON-LD address: addressLocality Kathmandu, addressRegion Bagmati Province, addressCountry NP, geo 27.7172 / 85.3240, areaServed Kathmandu, Nepal and Worldwide
- "Birgunj" may remain ONLY in the education entry "Birgunj Institute of Technology" (old college name).

## ALREADY DONE (do not redo)
- STEP A: titles, meta descriptions, canonicals, lang, hreflang removal, Kathmandu in meta/JSON-LD/text (commit 33ec524).
- STEP B-FIX: index.html hero restored, single H1 "Shamsudin Aalam" + hidden `.sr-only` keywords, tagline "Software Developer", tags closed, `.sr-only` CSS added (commit c2cd849).
- Nothing has been pushed. Live site is still the original.

## PROGRESS (update after each step)
- [x] STEP B: finish headings, links, accessibility, breadcrumbs, 404.html (all pages)
- [x] STEP C: JSON-LD, Open Graph, robots.txt, sitemap.xml, llms.txt, manifest, contact block
- [x] STEP R1: index.html resume content
- [x] STEP R2: about.html resume content
- [x] STEP R3: resume.html resume content
- [ ] STEP R4: projects.html resume content
- [ ] STEP R5: services.html resume content
- [ ] STEP R6: footer/contact + role wording + SEO text consistency on all pages
- [ ] STEP D: images
- [ ] STEP E: JS/CSS performance, static content
- [ ] STEP F: headers, Cloudflare notes, final verification

---

## STEP B: Headings, links, accessibility (finish for all 5 pages)
1. HEADINGS: exactly one H1 per page (first in main content), then H2 sections, H3 subsections, no skipped levels. Card titles, skill names and labels that are not real headings become `<p>`/`<span>`/`<strong>` with CSS classes that keep the exact same look (reuse the existing `bix-hN` approach). index.html: the H1 is done; verify the rest of its hierarchy (H2/H3, no skipped levels).
2. H1 RULE: keep the ORIGINAL visible heading text and style on every page. Add SEO keywords only in a `.sr-only` span inside the H1 (about, projects, resume, services: original visible title + hidden " - Software Developer in Kathmandu, Nepal"). NEVER enlarge or restyle a visible H1. If an inner page has no visible H1, use the existing page-title/breadcrumb title element as the H1 without changing its look.
3. LINKS (all pages, including index.html): add `rel="noopener noreferrer"` to every `target="_blank"`; `nofollow` for non-essential third-party links. No empty anchors (add text, or aria-label + title on icon links). Unique descriptive anchor texts (no "click here"/"read more").
4. Add visible breadcrumbs on inner pages (matching the site style; reuse the existing inner-banner/breadcrumb area if present) and footer links to all main pages. Create `404.html` in the site style.
5. ACCESSIBILITY: semantic header/nav/main/section/footer, skip link (visually hidden until focused), aria-labels, doctype first, charset first in head, no duplicate IDs.
6. Each of `</main>`, `</body>`, `</html>` exactly once on every page, WhatsApp button inside `<body>`.
7. Compare each page with `origin/master` for visual identity. Tick STEP B, commit, STOP.

## STEP C: Structured data, social, crawl files, contact
1. JSON-LD: ONE `@graph` per page with Person (jobTitle "Software Developer", url, image, sameAs = Facebook, X, Instagram, LinkedIn, GitHub, telephone, email), WebSite, WebPage/ProfilePage, ProfessionalService, BreadcrumbList on inner pages. Remove CollegeOrUniversity and the duplicate Organization. Use the address/geo from PROJECT FACTS. Validate JSON syntax.
2. OPEN GRAPH / TWITTER: og:title, og:description, og:url (same as canonical), og:image (absolute URL, 1200x630, create `assets/og-image.png` if missing), og:type, og:site_name, twitter:card summary_large_image, twitter:title/description/image, matching the new title and description.
3. robots.txt: allow all incl. AI crawlers, remove blocking Disallow, include `Sitemap: https://shamsudinaalam.com.np/sitemap.xml`.
4. sitemap.xml: only real public pages, canonical non-www https URLs, lastmod, priority. Remove dead entries (single-project, blog, blog-detail).
5. Create `llms.txt` (short summary: who I am, services, key pages, contact) and `llms-full.txt`.
6. `site.webmanifest`: fix name, short_name, icon paths. Keep theme-color, favicon, apple-touch-icon.
7. Footer/contact block on all pages: "Kathmandu, Nepal", mailto and tel links. No invented street address.

## STEP R (R1 to R6): Resume content and role wording
General rules for ALL R steps:
- Do ONE sub-step (R1, R2, ...) per run, then commit and STOP.
- Change only text content. Keep HTML structure, classes, IDs, animations and CSS. If a section has fewer/more items than the resume, COPY an existing item's markup and fill it with the new text. Do not invent new designs.
- Process for every page: (a) read the whole page; (b) write me a short table "current text vs resume text" for each section; (c) edit; (d) VERIFY by grepping the page that every required resume string for that page (listed in its sub-step) is really present, and print the result as a checklist (found / missing). Do not tick the step if anything is missing.
- Use the wording of RESUME DATA below exactly. Only shorten if it does not fit the card layout, and list every shortened item in the report.
- Old items not in the resume: on resume.html and about.html (experience, education, skills, certifications) the resume REPLACES outdated entries (old text stays recoverable in git history; list what you removed). On index.html, projects.html and services.html keep old items and list them under "Not in resume - decide".
- Never add new outbound links. Existing live-project links stay.

### Role wording
- Main role = "Software Developer". Where a specialty is needed: "Software Developer specializing in Laravel & PHP".
- Replace "Laravel Backend Developer" / "Laravel Developer" used as my main title with that wording. Real job titles inside the experience timeline stay "Laravel (PHP) Developer" as in the resume.
- Replace "5+ years" and "Full Stack Designer"-style claims with "3+ years" and "Software Developer".
- Keep the phrase "Laravel developer" at least once in the home meta description and in the about text.
- Do NOT put Django or Python in titles, H1, meta descriptions or og tags. They appear only in the skills list and the about text as "currently learning".

### RESUME DATA (source of truth)
SUMMARY: Software Developer specializing in Laravel & PHP with 3+ years of experience building production-grade APIs, enterprise web applications, and third-party integrations (Amadeus, DHL, FedEx, payment gateways). Currently developing a banking audit system for Shangrila Bank, with hands-on experience in Docker containerization and GitLab CI/CD pipelines for automated deployment. Specialized in MySQL and PostgreSQL optimization, RESTful API development, and server deployment on DigitalOcean/Ubuntu. Frontend collaboration experience with Vue.js and Bootstrap.
ABOUT-ONLY EXTRA LINE: "I am also currently learning Python and Django to broaden my backend skills."

EXPERIENCE (newest first)
1. Laravel (PHP) Developer, Trilokya Technology Pvt Ltd, Kathmandu, Nepal, June 2026 - Present
   - Developing and maintaining the Audit System for Shangrila Bank, a Laravel-based enterprise application for managing bank audit workflows and compliance records.
   - Containerized the application using Docker to ensure consistent environments across development, staging, and production.
   - Set up and maintained CI/CD pipelines on GitLab for automated build, testing, and deployment, reducing manual release effort.
2. Laravel (PHP) Developer, Nectar Digit Pvt Ltd, Kathmandu, Nepal, June 2024 - June 2026
   - Developed and maintained 10+ Laravel web applications serving thousands of users with optimized backend performance and scalable architecture.
   - Designed and implemented RESTful APIs consumed by frontend applications (Vue.js), including debugging and performance optimization.
   - Deployed and managed Laravel applications on DigitalOcean, Hostinger, and CyberPanel ensuring stable and reliable performance.
   - Performed database optimization using indexing, Caching, and eager loading to improve application performance.
3. Laravel Developer (Remote), Des Vu Technologies, Pokhara, Nepal (Remote), November 2023 - May 2024
   - Contributed to backend development of a travel platform of Sayatri using Laravel and MySQL.
   - Worked under senior developers to implement API integrations and booking workflows.
4. Laravel Developer (Part-time), Prosoft Nepal, Tinkune, Kathmandu, June 2023 - September 2023
   - Contributed to multiple client projects focusing on backend development and database design.
   - Implemented admin dashboards, RESTful APIs, and role-based user management features.

EDUCATION
- B.Sc. (Hons) in Information Technology, 2026 - Present, LBEF Campus (Affiliated with Asia Pacific University of Technology & Innovation), Kathmandu, Nepal
- Diploma in Computer Science and Engineering, GPA 3.5/4.0, 2019 - 2023, Birgunj Institute of Technology, Birgunj, Nepal

PROJECTS
1. Shangrila Bank Audit System (2026) - Laravel, MySQL, Docker, GitLab CI/CD
   - Building an enterprise audit management system for Shangrila Bank to digitize and streamline internal audit workflows and compliance reporting.
   - Containerized the app with Docker and built a GitLab CI/CD pipeline for automated testing and deployment across environments.
   - (No public link and NO outbound links: private bank network.)
2. Order E-commerce Platform (2024) - Laravel, MySQL, Bootstrap, Vue.js
   - Developed a full-featured e-commerce platform with Vue.js frontend and efficient order management for seamless shopping experiences.
   - Integrated secure payment gateways and optimized inventory workflows using efficient database queries to ensure reliable product availability.
3. Sewa Travel Booking Platform (2025) - Laravel, MySQL, Bootstrap, Vue.js
   - Developed a travel booking platform with secure workflows for domestic and international flights.
   - Integrated Amadeus and Plazmatech SOAP APIs for flight availability and booking management.
4. Elite Express Cargo Platform (2025) - Laravel, MySQL, Bootstrap
   - Developed a cargo and courier management platform with efficient service workflows and customer tracking features using Laravel.
   - Integrated DHL, FedEx, and other courier APIs for live shipment status updates.
5. Kantipur Theatre Ticketing Platform (2024) - Laravel, MySQL, Bootstrap
   - Built an online theatre ticket booking platform with show management for performances and movie screenings.
   - Integrated eSewa and Khalti payment gateways with automated booking confirmations.
6. Lekhabidhi HR Management System (2024) - Laravel, MySQL, Bootstrap, Vue.js
   - Developed a scalable HR management system handling attendance, payroll, employee records, and organizational workflows.
   - Implemented role-based access control, leave management, and efficient HR operations tracking.

SKILLS
- Backend: PHP, Laravel, RESTful APIs, SOAP API integration, Python and Django (currently learning)
- Database: MySQL, PostgreSQL
- Deployment & DevOps: Docker, GitLab CI/CD, Ubuntu Linux, DigitalOcean, Nginx, Apache, cPanel, CloudPanel, SSH
- API & Integrations: Amadeus, DHL, FedEx, Plazmatech SOAP, eSewa, Khalti, ConnectIPS, HBL, Fonepay, Stripe, PayPal
- Frontend Collaboration: Vue.js, Bootstrap, jQuery, AJAX
- Developer Tools: Git, GitHub, GitLab, Postman, Composer, VS Code, TablePlus, FileZilla, XAMPP
- Other: SEO Optimization, Google Search Console, FFmpeg, Zoho Mail, Slack
Progress bars/percentages: keep existing values for skills that already exist. For new skills reuse a similar existing value, EXCEPT Python and Django: use a LOW value (about 30%) and label them "(Learning)". List every new skill and its percentage in the report so I can review.

CERTIFICATIONS
- Laravel Advanced: Building Real-World Applications - Udemy
- Built a Food Ordering E-commerce Platform using Laravel - Udemy (Instructor: Web Coding)
- Vue.js Complete Guide for Beginners to Advanced - Udemy (Instructor: Maximilian)

EXTRACURRICULAR
- Volunteered in local coding workshops, promoting learning and teamwork among students.
- Participated in tech competitions and collaborated with peers to solve programming challenges.

### R1: index.html
Update hero bio/short summary (mention Laravel & PHP), counters (3+ years, 10+ web applications), skills section (with Python/Django as learning), featured projects, short experience/education if shown.
Required strings to verify: "3+", "10+", "Software Developer", "Laravel", "Django", the 6 project titles if projects are shown.

### R2: about.html
Full SUMMARY, ABOUT-ONLY EXTRA LINE, experience timeline (4 jobs with dates and bullets), education (2 entries), certifications (3), extracurricular (2), skills if shown.
Required strings: "Trilokya Technology", "Nectar Digit", "Des Vu Technologies", "Prosoft Nepal", "June 2026", "June 2024", "November 2023", "June 2023", "LBEF Campus", "Birgunj Institute of Technology", "3.5/4.0", "Udemy", "Maximilian", "learning Python and Django".

### R3: resume.html (this page was NOT updated before; do it carefully)
Experience (4 jobs, all bullets), education (2), skills (all 7 categories incl. Python/Django learning), certifications (3), extracurricular if the page has a place for it (otherwise skip and tell me). Remove outdated entries that conflict and list them in the report. The resume download button must point to `assets/shamsudin-resume.pdf` (same filename that exists now; do not touch the file).
Required strings: all required strings from R2, plus "Shangrila Bank", "Docker", "GitLab CI/CD", "PostgreSQL", "Amadeus", "eSewa", "Khalti", "ConnectIPS", "Fonepay", "Stripe", "PayPal", "CloudPanel", "TablePlus", "Google Search Console", "FFmpeg", "Zoho Mail", "Slack", "Python", "Django".

### R4: projects.html
Make sure the 6 resume projects exist as cards with title, year, tech stack and the two bullets of description. If a card with the same project already exists, update its text; otherwise copy an existing card's markup. Keep existing cards, filters and category buttons working; use the closest existing category. Keep existing live links, add none. Shangrila project: text only.
Required strings: the 6 project titles, "Amadeus", "DHL", "eSewa", "Khalti", "role-based access control".

### R5: services.html
Rewrite service wording to match real skills, keeping layout and accordion: Laravel web application development, REST API development, third-party API and payment gateway integration (Amadeus, DHL, FedEx, eSewa, Khalti, Stripe, PayPal), deployment and DevOps (Docker, GitLab CI/CD, DigitalOcean, Ubuntu, Nginx), database design and optimization (MySQL, PostgreSQL). Old services not matching (for example graphic design) are kept and listed under "Not in resume - decide".
Required strings: "REST API", "Docker", "PostgreSQL", "payment".

### R6: footer/contact, role wording, SEO text consistency (all 5 pages + llms files + manifest)
- Footer/contact: mailto, tel, "Kathmandu, Nepal".
- Apply the Role wording rules everywhere (hero, about, resume, services, footer, titles, descriptions, H1 hidden text, og/twitter, JSON-LD, llms.txt, llms-full.txt, site.webmanifest).
- JSON-LD: Person.jobTitle "Software Developer"; knowsAbout = Software Development, Laravel, PHP, REST API, MySQL, PostgreSQL, Docker, GitLab CI/CD, Vue.js, Python, Django; alumniOf = LBEF Campus, Birgunj Institute of Technology; telephone and email on Person and ProfessionalService.
- Re-check title (50-60 chars) and meta description (120-160 chars) on every page.
- FINAL REPORT for all of Step R: files/sections changed; "Not in resume - decide" list; removed outdated entries; new skills with percentages; shortened items; structure mismatches and choices made. Also print the WhatsApp number in the index.html wa.me link so I can verify it.

## STEP D: Images (do this alone)
1. Start with the largest files (project/*.png, hero/newpic.jpg, hire/bg.png) and CSS backgrounds (hire/bg.png, breadcrumb/bg.jpg, shapes). Convert to WebP, resize (hero max ~1600px, cards ~800px), quality 70-80%.
2. Add width/height to every `<img>`, `loading="lazy"` + `decoding="async"` to below-the-fold images, unique descriptive alt (decorative = `alt=""`). Check that width/height do not distort images (keep aspect ratio and existing CSS sizing).
3. Hero image: NOT lazy, `fetchpriority="high"` and `<link rel="preload" as="image">`.
4. Keep original files until everything works. Update all references in HTML and CSS. Report before/after total size (target under 3 MB per page).

## STEP E: JS/CSS performance and static content
1. Defer non-critical scripts, consolidate the duplicate style.css include (preload + link), async non-critical CSS, preconnect for fonts/CDNs, font-display: swap.
2. Remove unused libraries (Vue is not used). Load Tawk.to, reCAPTCHA, FancyBox, Owl only when needed (interaction or after window load/idle).
3. Move inline `style=""` attributes and the inline `<style>` block into the CSS file.
4. Verify all important text (headings, bio, skills, services, projects) is in static HTML; JS only enhances.
5. Do not break any slider, popup, filter, counter, typing animation or contact form. Test each.

## STEP F: Headers, Cloudflare notes, verification
1. Create `_headers` and a `README-DEPLOY.md` with Cloudflare cache rules (images/CSS/JS/fonts 1 year immutable, HTML short cache) and the www -> non-www 301 redirect.
2. VERIFY with a script: every page has one unique title (50-60 chars), one meta description (120-160 chars), one H1, correct heading order, self-canonical, no images without alt/width/height, no empty anchors, no www/http URLs, no remaining "Birgunj / Province 2 / Madhesh / NP-2 / 27.0058 / 84.8764" (except the college name).
3. Validate HTML, JSON-LD, sitemap.xml, robots.txt. Run Lighthouse mobile + desktop if available and report scores and final page weight.
4. List the manual tasks for me: SPF/DMARC DNS records, Cloudflare settings, Search Console sitemap + request indexing, social profile locations set to Kathmandu, resume PDF replaced, backlinks.