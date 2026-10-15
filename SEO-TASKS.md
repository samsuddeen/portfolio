You are a senior technical SEO engineer and front-end performance expert. Fix ALL SEO issues in this static portfolio site (plain HTML, CSS, JavaScript; hosted on GitHub Pages behind Cloudflare). Domain: https://shamsudinaalam.com.np (NON-www is the canonical version). Owner: Shamsudin Aalam (also spelled Samsudin Alam), mid-level Laravel / Full Stack Web Developer & Designer from Birgunj, Nepal.

GOAL: On-page score above 90% in Seobility and an A grade in SEOptimer, WITHOUT changing the visual design, layout, or functionality. Work through the whole project (index.html, about.html, projects.html, resume.html, services.html and any others). Before editing, scan all files and list what you found. After editing, give me a changelog.

AUDIT FINDINGS TO FIX

1. TITLE TAG
- Seobility sees a title that is 849px wide (too long, limit 580px). SEOptimer sees a title of only 13 characters. The title is probably being changed by JavaScript, or the raw HTML has a leftover template title (e.g. "Himmelimherzen"). Find and remove any JS that sets document.title or any leftover template title.
- Put one static, unique <title> in the raw HTML of every page, 50-60 characters, with the main keywords first. Example for the home page: "Shamsudin Aalam | Laravel & Full Stack Developer Nepal". Make sure the title words also appear in the H1 and the page content.
- Use similar patterns for the other pages (About, Projects, Resume, Services), each unique.

2. META DESCRIPTION
- Currently 273 characters (limit 120-160 characters / ~1000px). Rewrite it for every page, unique per page, 140-158 characters, including "Laravel developer", "web applications" and "Nepal", with a soft call to action.
- Remove any JS that rewrites meta tags at runtime.

3. CANONICAL, HREFLANG, LANGUAGE
- The canonical currently points to https://www.shamsudinaalam.com.np/ but the site is served on the non-www domain. Change every canonical to the exact non-www HTTPS URL of that page (self-referencing). Make og:url, sitemap.xml and JSON-LD URLs consistent with it.
- hreflang: there are alternate links but no self-referencing one. Since the site is single-language, REMOVE all hreflang/alternate tags (or, if you keep one, add the self-referencing en one plus x-default).
- Language: use <html lang="en"> only. Remove <meta name="language" content="english"> or change it to "en". No non-ISO language values anywhere.

4. HEADING STRUCTURE
- The page currently has 46 headings: first heading is an H4, 1 H2, 2 H3, 27 H4, 17 H5, 2 H6, with skipped levels. The H1 "Shamsudin Aalam" is only 15 characters.
- Rebuild the hierarchy on every page: exactly one H1 first in the main content, then H2 for sections, H3 for subsections, no skipped levels. Convert card titles/skill names/labels that are not real headings into <p>, <span> or <strong> and keep their look with CSS classes (don't change the visuals).
- New H1 (20+ characters, keyword-rich) for home, e.g. "Shamsudin Aalam - Laravel Developer & Web Designer". Make the H1 contain the main title keywords.
- Make sure the main keywords (shamsudin aalam, laravel developer, web applications, full stack developer, Nepal) appear naturally in the title, meta description, H1 and H2s. No keyword stuffing.

5. IMAGES (page is 14.29 MB, images are 12.53 MB of it, 63 images, mobile LCP is 44 s)
- Convert all large JPG/PNG to WebP (keep fallback only if needed), resize to the real display size (max ~1600px wide for hero, ~800px for cards), compress to roughly 70-80% quality. Target total page weight under 3 MB.
- Use <picture>/srcset/sizes where useful.
- Add loading="lazy" and decoding="async" to every below-the-fold image. The first/hero image must NOT be lazy: add fetchpriority="high" and a <link rel="preload" as="image">.
- Add explicit width and height attributes to every <img> (fixes layout shift).
- Add descriptive, unique alt text to every image (1 image has none). Decorative images get alt="".
- Rename image files to descriptive kebab-case names if safe, and update all references.
- If any video/GIF/large background asset exists, compress it or lazy-load it.

6. RENDER-BLOCKING AND JS/CSS PERFORMANCE
- Add defer to all non-critical scripts; move scripts to end of body. Add rel="preconnect" for Google Fonts / CDNs, use font-display: swap, preload the main font.
- Load non-critical CSS asynchronously (media="print" onload swap or rel=preload) and inline only the small critical CSS for above-the-fold content.
- Detected libraries: Bootstrap, jQuery, Owl Carousel, FancyBox, Vue.js, reCAPTCHA, Tawk.to, Google Analytics. Check which are really used; remove unused ones, load heavy ones (Tawk.to, reCAPTCHA, FancyBox, Owl) only when needed (on interaction or after window load / idle). Remove unused CSS/JS where safe.
- Remove all inline style="" attributes and move them into CSS classes in the stylesheet.
- Make sure everything is minified.
- Mobile PageSpeed lab data: LCP 44.1 s, FCP 8.4 s, Speed Index 28.7 s, TTI 48.9 s. Aim for LCP under 2.5 s.

7. RENDERED CONTENT (GEO / LLM READABILITY)
- 21% of the content is injected by JavaScript (Vue/Owl etc.). Move all important text (headings, bio, skills, services, project names and descriptions) into the static HTML so crawlers and AI engines can read it without running JS. JS should only enhance.

8. LINKS
- 33 external links (72% of all links). Reduce unnecessary external links, keep only important ones (social profiles, live projects). Add rel="noopener noreferrer" to every target="_blank" link and rel="nofollow" for non-essential third-party links.
- 2 internal links have no anchor text: add visible text or aria-label (icon links need aria-label and title).
- Remove duplicate anchor texts: make each anchor text unique and descriptive (no "click here", "read more").
- Make link URLs friendly: if feasible for GitHub Pages, use clean URLs (/about/, /projects/ via folder/index.html) and update all internal links, canonicals, sitemap and OG URLs; otherwise keep .html and don't break existing URLs. Add a custom 404.html.
- Add a clear internal link structure: nav, footer links to all main pages, breadcrumbs on inner pages (with BreadcrumbList JSON-LD).

9. STRUCTURED DATA (JSON-LD)
- Keep one clean JSON-LD @graph per page: Person (Shamsudin Aalam, jobTitle, url, image, sameAs = Facebook, X, Instagram, LinkedIn, GitHub), WebSite, WebPage/ProfilePage, ProfessionalService (address locality Birgunj, region Province 2 / Madhesh, country NP, geo 27.0058, 84.8764).
- Remove wrong types such as CollegeOrUniversity and the duplicate Organization unless they are accurate.
- Validate the JSON syntax.

10. SOCIAL / OPEN GRAPH
- Update og:title, og:description, og:url, og:image (absolute URL, 1200x630), og:type, og:site_name, twitter:card=summary_large_image, twitter:title, twitter:description, twitter:image so they match the new title and description. Create the 1200x630 OG image if missing.

11. CRAWLING FILES
- robots.txt: allow all, allow major AI crawlers, include the line: Sitemap: https://shamsudinaalam.com.np/sitemap.xml
- sitemap.xml: list every public page with the canonical non-www URL, lastmod and priority. Remove any www or http URLs.
- Create llms.txt in the root (short summary of who I am, services, key pages, contact) and optionally llms-full.txt.
- Add site.webmanifest, theme-color meta, and keep apple-touch-icon and favicon.

12. LOCAL / CONTACT
- Add a visible contact block in the footer/contact section with city and country (Birgunj, Nepal), email as a mailto link or contact form link, and phone only if I provide one (leave a clearly marked TODO placeholder). Mirror the same data in JSON-LD.

13. ACCESSIBILITY / HTML QUALITY (also helps SEO)
- Use semantic tags: header, nav, main, section, article, footer. Add a skip link, aria-labels, lang attribute, correct doctype first in the file, charset UTF-8 first in head, viewport meta.
- Ensure no broken links, no duplicate IDs, valid HTML.

14. CACHING / HEADERS (static host)
- Add a _headers file (works on Cloudflare Pages/Netlify) and also document the exact Cloudflare Cache Rules I need to set manually: cache images, CSS, JS, fonts for 1 year (immutable, use hashed/versioned filenames), HTML short cache.
- Enable www -> non-www 301 redirect documentation for Cloudflare.

RULES
- Do not change design, colors, content meaning or functionality. Keep my wording; only improve where required by SEO.
- Keep a backup (git commit or copy) before big changes. Make small commits per task.
- Do not invent facts, phone numbers, addresses, reviews or clients. Use TODO comments for missing info.
- Keep all existing URLs working (if you rename, add redirects or keep old files).

VERIFY AT THE END
- Run Lighthouse (mobile + desktop) and report SEO, Performance, Accessibility, Best Practices scores before/after.
- Validate HTML, JSON-LD (Schema validator), sitemap and robots.txt.
- Check with a script that every page has: one unique title (50-60 chars), one meta description (120-160 chars), one H1, correct heading order, self-canonical, no images without alt/width/height, no empty anchors.
- Print the final page weight and a table of what changed per file.
- Finally list the tasks I must do manually outside the code (DNS records, Cloudflare settings, Search Console, backlinks).





ADDITIONAL TASK: LOCATION CHANGE (Birgunj -> Kathmandu)

I have moved from Birgunj to Kathmandu. Update the location everywhere in the project. Search the whole project (all .html, .js, .json, .xml, .txt, .webmanifest, .md files, meta tags, comments and JSON-LD) for "Birgunj", "Parsa", "Province 2", "Madhesh", "NP-2", "27.0058", "84.8764" and any other old-location text, then replace as follows:

1. VISIBLE TEXT
- Replace every "Birgunj" with "Kathmandu" (about section, hero, footer, contact section, resume, services, etc.).
- Replace "Birgunj, Nepal" with "Kathmandu, Nepal".
- If the text says "based in Birgunj" or similar, change it to "based in Kathmandu, Nepal". Keep the rest of the sentence as it is.

2. GEO META TAGS
- geo.region: NP-BA (Bagmati Province)
- geo.placename: Kathmandu
- geo.position: 27.7172;85.3240
- ICBM: 27.7172, 85.3240
- Remove the old NP-2, Birgunj and 27.0058;84.8764 values completely.

3. JSON-LD STRUCTURED DATA
- In Person, ProfessionalService and every other schema: addressLocality = "Kathmandu", addressRegion = "Bagmati Province", addressCountry = "NP".
- geo: latitude 27.7172, longitude 85.3240.
- If there is areaServed, set it to Kathmandu, Nepal and Worldwide (keep the global reach).
- Validate the JSON-LD syntax after the change.

4. SEO TEXT
- In title tags, meta descriptions, H1/H2s, alt texts, og:/twitter: tags and llms.txt, replace old-location keywords with "Kathmandu" where they appear. Keep "Nepal" in the titles too.
- If a keyword like "web developer in Birgunj" exists, change it to "web developer in Kathmandu". Add "Kathmandu" naturally to the home page description (without stuffing).
- Make sure the title and meta description stay within their length limits after the change (title 50-60 chars, description 120-160 chars).

5. CONTACT / LOCAL BLOCK
- The footer/contact block should say "Kathmandu, Nepal". Do NOT invent a street address, ward or phone number. If I want to show a more specific area, leave a TODO comment: 

6. FILES TO RECHECK
- llms.txt, llms-full.txt, sitemap.xml (update lastmod for edited pages), site.webmanifest, 404.html, resume text, and any downloadable resume PDF text (tell me if the PDF needs a manual update).

7. VERIFY
- Run a project-wide search at the end to confirm there is zero remaining mention of Birgunj / Province 2 / Madhesh / NP-2 / 27.0058 / 84.8764.
- Give me a list of the files and lines that were changed.