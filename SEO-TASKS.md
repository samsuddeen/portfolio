# SEO-TASKS.md (single source of truth)

## GLOBAL RULES (apply to every step)
- NEVER run `git push`, never deploy, never publish. Only LOCAL commits.
- Work on ONE step at a time. After finishing a step: tick its checkbox in the PROGRESS section, make a local commit, print a short changelog, then STOP and wait for me. Do not start the next step.
- Before starting a step: run `git status` and `git log --oneline -10`, and check what is already done so you only finish what is missing.
- Do not change design, colors, layout, CSS classes/IDs, animations or functionality unless the step says so.
- Do not invent facts, numbers, links, clients, addresses or images. Use `<!-- TODO -->` for missing info.
- Keep all existing .html URLs working (no clean URLs).
- Never add outbound links to auditsystemshangrilabank.com or audit.trilokyasoft.com (private bank system). Show that project as text only.
- If something is not in this file or you are unsure, ask me instead of guessing.

## PROJECT FACTS
- Site: https://shamsudinaalam.com.np (NON-www is canonical). Static HTML/CSS/JS on GitHub Pages behind Cloudflare.
- Pages: index.html, about.html, projects.html, resume.html, services.html
- Owner: Shamsudin Aalam (also spelled Samsudin Alam)
- Main role: **Software Developer** (specialty: Laravel & PHP). 3+ years experience.
- Location: **Kathmandu, Nepal** (public pages say only this; no street address)
- Phone: +977-9816266897 (tel: link) | Email: shamsudinaalam@gmail.com (mailto: link)
- Geo: geo.region NP-BA, geo.placename Kathmandu, geo.position 27.7172;85.3240, ICBM 27.7172, 85.3240
- JSON-LD address: addressLocality Kathmandu, addressRegion Bagmati Province, addressCountry NP, geo 27.7172 / 85.3240, areaServed Kathmandu, Nepal and Worldwide
- "Birgunj" may remain ONLY in the education entry "Birgunj Institute of Technology" (old college name).

## PROGRESS (update after each step)
- [x] STEP A: title, meta description, canonical, hreflang, language, location change in meta/JSON-LD/text
- [ ] STEP B: headings, links, accessibility, 404.html
- [ ] STEP C: JSON-LD, Open Graph, robots.txt, sitemap.xml, llms.txt, manifest, contact block
- [ ] STEP R: resume content + role wording
- [ ] STEP D: images
- [ ] STEP E: JS/CSS performance, static content
- [ ] STEP F: headers, Cloudflare notes, final verification

Note: Steps A and B may already be partly or fully done (done earlier with older wording). Check the code first. Step R will fix the role wording afterwards.

---

## STEP A: Meta, canonical, language, location
1. Delete orphan files `dist/index.html` and `Schema.org` only after a project-wide search shows nothing references them.
2. TITLE: one static unique `<title>` per page, 50-60 chars, keywords first. Home: `Shamsudin Aalam | Software Developer Kathmandu, Nepal`. Other pages: same pattern, each unique (About, Projects, Resume, Services). Title words must also appear in H1 and content.
3. META DESCRIPTION: unique per page, 120-160 chars, starts with "Software developer in Kathmandu, Nepal", mentions Laravel developer / PHP / REST APIs / web applications naturally, soft call to action. Keep the phrase "Laravel developer" at least once on the home meta description.
4. CANONICAL: every page self-referencing `https://shamsudinaalam.com.np/<page>.html` (non-www, https). Make og:url, sitemap and JSON-LD URLs consistent.
5. Remove all hreflang/alternate tags (single-language site).
6. LANGUAGE: `<html lang="en">` only. Remove `<meta name="language" content="English">` or set to `en`.
7. LOCATION: replace old Birgunj / Parsa / Province 2 / Madhesh / NP-2 / 27.0058 / 84.8764 values in visible text, geo meta tags and JSON-LD with the PROJECT FACTS values above.

## STEP B: Headings, links, accessibility
1. HEADINGS: exactly one H1 per page (first in main content), then H2 sections, H3 subsections, no skipped levels. Card titles, skill names and labels that are not real headings become `<p>`/`<span>`/`<strong>` with CSS classes that keep the exact same look.
2. Home H1: `Shamsudin Aalam - Software Developer (Laravel & PHP Specialist)`. Inner pages: unique keyword-rich H1, 20+ chars.
3. LINKS: add `rel="noopener noreferrer"` to every `target="_blank"`; `nofollow` for non-essential third-party links. No empty anchors (add text or aria-label + title on icon links). Unique descriptive anchor texts (no "click here"/"read more").
4. Add visible breadcrumbs on inner pages and footer links to all main pages. Create `404.html` matching the site style.
5. ACCESSIBILITY: semantic header/nav/main/section/footer, skip link, aria-labels, doctype first, charset first in head, no duplicate IDs.
6. Fix `</main>`, `</body>`, `</html>` so each appears exactly once, with the WhatsApp button inside `<body>` before the closing tag.

## STEP C: Structured data, social, crawl files, contact
1. JSON-LD: ONE `@graph` per page with Person (jobTitle "Software Developer", url, image, sameAs = Facebook, X, Instagram, LinkedIn, GitHub, telephone, email), WebSite, WebPage/ProfilePage, ProfessionalService, BreadcrumbList on inner pages. Remove CollegeOrUniversity and the duplicate Organization. Use the address/geo from PROJECT FACTS. Validate JSON syntax.
2. OPEN GRAPH / TWITTER: og:title, og:description, og:url, og:image (absolute, 1200x630, create `assets/og-image.png` if missing), og:type, og:site_name, twitter:card summary_large_image, twitter:title/description/image, matching the new title and description.
3. robots.txt: allow all incl. AI crawlers, remove blocking Disallow, include `Sitemap: https://shamsudinaalam.com.np/sitemap.xml`.
4. sitemap.xml: only real public pages, canonical non-www https URLs, lastmod, priority. Remove dead entries (single-project, blog, blog-detail).
5. Create `llms.txt` (short summary: who I am, services, key pages, contact) and `llms-full.txt`.
6. `site.webmanifest`: fix name, short_name, icon paths. Keep theme-color, favicon, apple-touch-icon.
7. Footer/contact block on all pages: "Kathmandu, Nepal", mailto and tel links. No invented street address.

## STEP R: Resume content and role wording
Change only text content. Keep HTML structure, classes, IDs and animations. If a section has fewer/more items than the resume, copy an existing item's markup. Anything on the site that is NOT in the resume must be kept and listed at the end under "Not in resume - decide".

### Role wording
- Main role = "Software Developer". Where a specialty is needed: "Software Developer specializing in Laravel & PHP".
- Replace "Laravel Backend Developer" / "Laravel Developer" used as my main title with that wording (hero, about, resume, services, footer, titles, descriptions, H1, og/twitter, JSON-LD, llms files, manifest).
- Replace "5+ years" and "Full Stack Designer"-style claims with "3+ years" and "Software Developer".
- Do NOT change real job titles in the experience timeline (they stay "Laravel (PHP) Developer").
- Re-check title (50-60 chars) and meta description (120-160 chars) afterwards.
- JSON-LD: knowsAbout = Software Development, Laravel, PHP, REST API, MySQL, PostgreSQL, Docker, GitLab CI/CD, Vue.js; alumniOf = LBEF Campus, Birgunj Institute of Technology.

### Resume data (source of truth)
SUMMARY: Software Developer specializing in Laravel & PHP with 3+ years of experience building production-grade APIs, enterprise web applications, and third-party integrations (Amadeus, DHL, FedEx, payment gateways). Currently developing a banking audit system for Shangrila Bank, with hands-on experience in Docker containerization and GitLab CI/CD pipelines for automated deployment. Specialized in MySQL and PostgreSQL optimization, RESTful API development, and server deployment on DigitalOcean/Ubuntu. Frontend collaboration experience with Vue.js and Bootstrap.

EXPERIENCE (newest first)
1. Laravel (PHP) Developer, Trilokya Technology Pvt Ltd, Kathmandu, Nepal, June 2026 - Present
   - Developing and maintaining the Audit System for Shangrila Bank, a Laravel-based enterprise application for managing bank audit workflows and compliance records.
   - Containerized the application using Docker for consistent environments across development, staging and production.
   - Set up and maintained CI/CD pipelines on GitLab for automated build, testing and deployment, reducing manual release effort.
2. Laravel (PHP) Developer, Nectar Digit Pvt Ltd, Kathmandu, Nepal, June 2024 - June 2026
   - Developed and maintained 10+ Laravel web applications serving thousands of users with optimized backend performance and scalable architecture.
   - Designed and implemented RESTful APIs consumed by Vue.js frontend applications, including debugging and performance optimization.
   - Deployed and managed Laravel applications on DigitalOcean, Hostinger and CyberPanel for stable performance.
   - Performed database optimization using indexing, caching and eager loading.
3. Laravel Developer (Remote), Des Vu Technologies, Pokhara, Nepal (Remote), November 2023 - May 2024
   - Contributed to backend development of the Sayatri travel platform using Laravel and MySQL.
   - Worked under senior developers on API integrations and booking workflows.
4. Laravel Developer (Part-time), Prosoft Nepal, Tinkune, Kathmandu, June 2023 - September 2023
   - Contributed to multiple client projects focusing on backend development and database design.
   - Implemented admin dashboards, RESTful APIs and role-based user management.

EDUCATION
- B.Sc. (Hons) in Information Technology, 2026 - Present, LBEF Campus (Affiliated with Asia Pacific University of Technology & Innovation), Kathmandu, Nepal
- Diploma in Computer Science and Engineering, GPA 3.5/4.0, 2019 - 2023, Birgunj Institute of Technology, Birgunj, Nepal

PROJECTS
1. Shangrila Bank Audit System (2026) - Laravel, MySQL, Docker, GitLab CI/CD. Enterprise audit management system to digitize internal audit workflows and compliance reporting. Docker + GitLab CI/CD pipeline for automated testing and deployment. (No public link.)
2. Order E-commerce Platform (2024) - Laravel, MySQL, Bootstrap, Vue.js. Full-featured e-commerce platform with Vue.js frontend and efficient order management. Secure payment gateways, optimized inventory workflows.
3. Sewa Travel Booking Platform (2025) - Laravel, MySQL, Bootstrap, Vue.js. Travel booking with secure workflows for domestic and international flights. Integrated Amadeus and Plazmatech SOAP APIs.
4. Elite Express Cargo Platform (2025) - Laravel, MySQL, Bootstrap. Cargo and courier management with customer tracking. Integrated DHL, FedEx and other courier APIs for live shipment status.
5. Kantipur Theatre Ticketing Platform (2024) - Laravel, MySQL, Bootstrap. Online theatre ticket booking with show management. Integrated eSewa and Khalti with automated booking confirmations.
6. Lekhabidhi HR Management System (2024) - Laravel, MySQL, Bootstrap, Vue.js. HR system for attendance, payroll, employee records. Role-based access control, leave management.
(Existing projects that already have a live URL keep their links. Do not add new links.)

SKILLS
- Backend: PHP, Laravel, RESTful APIs, SOAP API integration
- Database: MySQL, PostgreSQL
- Deployment & DevOps: Docker, GitLab CI/CD, Ubuntu Linux, DigitalOcean, Nginx, Apache, cPanel, CloudPanel, SSH
- API & Integrations: Amadeus, DHL, FedEx, Plazmatech SOAP, eSewa, Khalti, ConnectIPS, HBL, Fonepay, Stripe, PayPal
- Frontend Collaboration: Vue.js, Bootstrap, jQuery, AJAX
- Developer Tools: Git, GitHub, GitLab, Postman, Composer, VS Code, TablePlus, FileZilla, XAMPP
- Other: SEO Optimization, Google Search Console, FFmpeg, Zoho Mail, Slack
(Keep existing progress-bar percentages for existing skills; for new skills reuse a similar value and list them for me.)

CERTIFICATIONS
- Laravel Advanced: Building Real-World Applications - Udemy
- Built a Food Ordering E-commerce Platform using Laravel - Udemy (Instructor: Web Coding)
- Vue.js Complete Guide for Beginners to Advanced - Udemy (Instructor: Maximilian)

EXTRACURRICULAR
- Volunteered in local coding workshops, promoting learning and teamwork among students.
- Participated in tech competitions and collaborated with peers to solve programming challenges.

### Where to update
1. index.html: hero role line ("Software Developer"), short bio (mention Laravel & PHP), counters (3+ years, 10+ web applications), skills, featured projects.
2. about.html: summary, experience timeline, education, certifications, extracurricular.
3. resume.html: experience, education, skills, certifications. Resume download button points to the PDF in assets/ (same filename as before; I replace the file myself).
4. projects.html: the 6 projects. Keep filters working; use the closest existing category.
5. services.html: wording aligned with real skills (Laravel web applications, REST API development, third-party API and payment integration, deployment and DevOps with Docker/GitLab CI/CD, database optimization). Keep layout and accordion.
6. Footer/contact on all pages: mailto, tel, "Kathmandu, Nepal".

### Final report for Step R
Files/sections changed; "Not in resume - decide" list; new skills needing percentage review; any structure mismatch where you made a choice. Also tell me the WhatsApp number in index.html (wa.me link) so I can verify it.

## STEP D: Images (do this alone)
1. Start with the largest files (project/*.png, hero/newpic.jpg, hire/bg.png) and CSS backgrounds (hire/bg.png, breadcrumb/bg.jpg, shapes). Convert to WebP, resize (hero max ~1600px, cards ~800px), quality 70-80%.
2. Add width/height to every `<img>`, `loading="lazy"` + `decoding="async"` to below-the-fold images, unique descriptive alt (decorative = `alt=""`).
3. Hero image: NOT lazy, `fetchpriority="high"` and `<link rel="preload" as="image">`.
4. Keep original files until everything works. Update all references in HTML and CSS. Report before/after total size (target under 3 MB per page).

## STEP E: JS/CSS performance and static content
1. Defer non-critical scripts, consolidate the duplicate style.css include (preload + link), async non-critical CSS, preconnect for fonts/CDNs, font-display: swap.
2. Remove unused libraries (Vue is not used). Load Tawk.to, reCAPTCHA, FancyBox, Owl only when needed (interaction or after window load/idle).
3. Move inline `style=""` attributes and the inline `<style>` block into the CSS file.
4. Verify all important text (headings, bio, skills, services, projects) is in static HTML; JS only enhances.
5. Do not break any slider, popup, filter, counter or animation. Test each.

## STEP F: Headers, Cloudflare notes, verification
1. Create `_headers` and a `README-DEPLOY.md` with Cloudflare cache rules (images/CSS/JS/fonts 1 year immutable, HTML short cache) and the www -> non-www 301 redirect.
2. VERIFY with a script: every page has one unique title (50-60 chars), one meta description (120-160 chars), one H1, correct heading order, self-canonical, no images without alt/width/height, no empty anchors, no www/http URLs, no remaining "Birgunj / Province 2 / Madhesh / NP-2 / 27.0058 / 84.8764" (except the college name).
3. Validate HTML, JSON-LD, sitemap.xml, robots.txt. Run Lighthouse mobile + desktop if available and report scores and final page weight.
4. List the manual tasks for me: SPF/DMARC DNS records, Cloudflare settings, Search Console sitemap + request indexing, social profile locations set to Kathmandu, resume PDF replaced, backlinks.