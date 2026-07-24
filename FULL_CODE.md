# Full website code
Every text-based file is reproduced below in full. Binary `.webp` image files are included in the ZIP and use the exact filenames documented in `IMAGE_PROMPTS.md`.

## `_config.yml`

```yaml
title: Michael Doe Counselling
short_title: Michael Doe
email: hello@michaeldoecounselling.co.uk
phone: "0161 000 0000"
description: Calm, relational counselling for adults in Stockport and online.
url: https://alexanderwatsoncounselling.co.uk
baseurl: ""
location: Stockport, Greater Manchester
form_endpoint: https://formspree.io/f/REPLACE_ME
demo: true
markdown: kramdown
permalink: pretty
exclude:
  - README.md
  - IMAGE_PROMPTS.md
  - FULL_CODE.md
  - michael-doe-premium-site.zip

```

## `_layouts/default.html`

```html
<!doctype html>
<html lang="en-GB">
  <head>
    {% include head.html %}
  </head>
  <body class="{{ page.body_class | default: 'page' }}">
    <a class="skip-link" href="#main-content">Skip to main content</a>
    {% include header.html %}
    <main id="main-content" tabindex="-1">
      {{ content }}
    </main>
    {% include footer.html %}
    <script src="{{ '/assets/js/main.js' | relative_url }}" defer></script>
  </body>
</html>

```

## `_includes/head.html`

```html
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#F8F6F2">
{% if site.demo %}<meta name="robots" content="noindex, nofollow, noarchive">{% endif %}

{% assign page_title = page.title | default: site.title %}
{% assign page_description = page.description | default: site.description %}
{% assign canonical_path = page.url | default: '/' %}

<title>{% if page.title %}{{ page.title }} · {{ site.short_title }}{% else %}{{ site.title }}{% endif %}</title>
<meta name="description" content="{{ page_description | escape }}">
<link rel="canonical" href="{{ canonical_path | absolute_url }}">

<meta property="og:type" content="website">
<meta property="og:locale" content="en_GB">
<meta property="og:site_name" content="{{ site.title }}">
<meta property="og:title" content="{{ page_title | escape }}">
<meta property="og:description" content="{{ page_description | escape }}">
<meta property="og:url" content="{{ canonical_path | absolute_url }}">
<meta property="og:image" content="{{ page.social_image | default: '/assets/images/og-image.webp' | absolute_url }}">
<meta name="twitter:card" content="summary_large_image">

<link rel="icon" href="{{ '/assets/images/favicon.svg' | relative_url }}" type="image/svg+xml">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Instrument+Serif:ital@0;1&family=Manrope:wght@400;500;600;700&display=swap" rel="stylesheet">
<link rel="stylesheet" href="{{ '/assets/css/main.css' | relative_url }}">

<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "ProfessionalService",
  "name": "{{ site.title }}",
  "url": "{{ site.url }}{{ site.baseurl }}",
  "description": "{{ site.description | escape }}",
  "areaServed": "{{ site.location }}",
  "email": "{{ site.email }}",
  "telephone": "{{ site.phone }}"
}
</script>

```

## `_includes/header.html`

```html
<header class="site-header" data-header>
  <div class="shell header-inner">
    <a class="brand" href="{{ '/' | relative_url }}" aria-label="{{ site.title }} home">
      <span class="brand-mark" aria-hidden="true">MD</span>
      <span class="brand-copy">
        <span class="brand-name">Michael Doe</span>
        <span class="brand-discipline">Counselling</span>
      </span>
    </a>

    <button class="nav-toggle" type="button" aria-expanded="false" aria-controls="primary-navigation" data-nav-toggle>
      <span class="nav-toggle-label">Menu</span>
      <span class="nav-toggle-lines" aria-hidden="true"><span></span><span></span></span>
    </button>

    <nav class="primary-nav" id="primary-navigation" aria-label="Primary" data-nav>
      <a href="{{ '/support/' | relative_url }}" {% if page.url == '/support/' %}aria-current="page"{% endif %}>Support</a>
      <a href="{{ '/how-i-work/' | relative_url }}" {% if page.url == '/how-i-work/' %}aria-current="page"{% endif %}>How it works</a>
      <a href="{{ '/first-session/' | relative_url }}" {% if page.url == '/first-session/' %}aria-current="page"{% endif %}>First session</a>
      <a href="{{ '/about/' | relative_url }}" {% if page.url == '/about/' %}aria-current="page"{% endif %}>About</a>
      <a class="nav-cta" href="{{ '/contact/' | relative_url }}" {% if page.url == '/contact/' %}aria-current="page"{% endif %}>Get in touch</a>
    </nav>
  </div>

  {% if site.demo %}
  <div class="demo-bar">
    <div class="shell"><strong>Demo website template — not a real counselling service.</strong> Every word, image, fee and professional detail must be replaced and verified before launch.</div>
  </div>
  {% endif %}
</header>

```

## `_includes/footer.html`

```html
<section class="crisis-strip" aria-labelledby="urgent-support-title">
  <div class="shell crisis-grid">
    <div>
      <p class="eyebrow eyebrow-light">Urgent support</p>
      <h2 id="urgent-support-title">This practice is not an emergency service.</h2>
    </div>
    <p>If you or someone else is in immediate danger, call <strong>999</strong> or go to A&amp;E. For urgent mental health help that is not an emergency, use NHS 111 online or call 111 and select the mental health option. Samaritans are available free on <strong>116 123</strong>.</p>
  </div>
</section>

<footer class="site-footer">
  <div class="shell footer-grid">
    <div class="footer-intro">
      <a class="brand brand-footer" href="{{ '/' | relative_url }}">
        <span class="brand-mark" aria-hidden="true">MD</span>
        <span class="brand-copy">
          <span class="brand-name">Michael Doe</span>
          <span class="brand-discipline">Counselling</span>
        </span>
      </a>
      <p>Calm, relational counselling for adults in Stockport and online.</p>
    </div>

    <div>
      <p class="footer-heading">Explore</p>
      <ul class="footer-links">
        <li><a href="{{ '/support/' | relative_url }}">Support</a></li>
        <li><a href="{{ '/how-i-work/' | relative_url }}">How it works</a></li>
        <li><a href="{{ '/first-session/' | relative_url }}">First session</a></li>
        <li><a href="{{ '/about/' | relative_url }}">About</a></li>
      </ul>
    </div>

    <div>
      <p class="footer-heading">Contact</p>
      <ul class="footer-links">
        <li><a href="mailto:{{ site.email }}">{{ site.email }}</a></li>
        <li><a href="tel:+441610000000">{{ site.phone }}</a></li>
        <li>{{ site.location }}</li>
      </ul>
    </div>

    <div>
      <p class="footer-heading">Information</p>
      <ul class="footer-links">
        <li><a href="{{ '/privacy/' | relative_url }}">Privacy</a></li>
        <li><a href="{{ '/contact/' | relative_url }}">Enquiries</a></li>
      </ul>
    </div>
  </div>

  <div class="shell footer-bottom">
    <p>© <span data-current-year>2026</span> {{ site.title }}.</p>
    {% if site.demo %}<p>Demonstration content only.</p>{% endif %}
  </div>
</footer>

```

## `assets/css/main.css`

```css
:root {
  --off-white: #f8f6f2;
  --paper: #fcfbf8;
  --charcoal: #2f3333;
  --charcoal-deep: #202424;
  --sage: #7a8b7b;
  --sage-pale: #e7ebe5;
  --muted: #6b6e6e;
  --stone: #d4d1cb;
  --stone-pale: #efede8;
  --white: #ffffff;
  --danger: #6f2f2f;
  --font-display: "Instrument Serif", Georgia, serif;
  --font-body: "Manrope", Arial, sans-serif;
  --shell: 1380px;
  --content: 760px;
  --section-space: clamp(5rem, 9vw, 9rem);
  --gutter: clamp(1.25rem, 4vw, 4.5rem);
  --border: 1px solid var(--stone);
}

* { box-sizing: border-box; }
html { scroll-behavior: smooth; }
body {
  margin: 0;
  background: var(--off-white);
  color: var(--charcoal);
  font-family: var(--font-body);
  font-size: 1rem;
  line-height: 1.75;
  -webkit-font-smoothing: antialiased;
  text-rendering: optimizeLegibility;
}
body.nav-open { overflow: hidden; }
img { display: block; max-width: 100%; height: auto; }
a { color: inherit; text-underline-offset: 0.2em; }
button, input, select, textarea { font: inherit; }
button { color: inherit; }
main:focus { outline: none; }

::selection { background: var(--sage); color: var(--white); }

.skip-link {
  position: fixed;
  left: 1rem;
  top: 1rem;
  z-index: 999;
  transform: translateY(-160%);
  background: var(--charcoal);
  color: var(--white);
  padding: 0.75rem 1rem;
  text-decoration: none;
}
.skip-link:focus { transform: translateY(0); }

.shell {
  width: min(100% - (var(--gutter) * 2), var(--shell));
  margin-inline: auto;
}

h1, h2, h3, p, blockquote, figure, ul, ol, dl { margin-top: 0; }
h1, h2, h3 {
  font-family: var(--font-display);
  font-weight: 400;
  line-height: 0.98;
  letter-spacing: -0.025em;
}
h1 { font-size: clamp(4rem, 8vw, 8.5rem); margin-bottom: 2rem; max-width: 11ch; }
h2 { font-size: clamp(2.75rem, 5vw, 5.5rem); margin-bottom: 1.8rem; }
h3 { font-size: clamp(1.7rem, 2.3vw, 2.5rem); line-height: 1.05; margin-bottom: 0.8rem; }
p { margin-bottom: 1.25rem; }

.eyebrow {
  margin-bottom: 1.35rem;
  color: var(--sage);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 0.14em;
  line-height: 1.4;
  text-transform: uppercase;
}
.eyebrow::after {
  content: "";
  display: block;
  width: 2.75rem;
  margin-top: 0.85rem;
  border-top: 1px solid currentColor;
}
.eyebrow-light { color: #bac5ba; }

.hero-lede,
.prose-large {
  font-size: clamp(1.1rem, 1.4vw, 1.28rem);
  line-height: 1.75;
}
.hero-lede { max-width: 39rem; color: var(--muted); }

.button-row {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 1rem 1.75rem;
  margin-top: 2.4rem;
}
.button {
  display: inline-flex;
  min-height: 3.5rem;
  align-items: center;
  justify-content: center;
  padding: 0.85rem 1.4rem;
  border: 1px solid transparent;
  font-size: 0.91rem;
  font-weight: 700;
  line-height: 1.2;
  text-decoration: none;
  transition: background-color 180ms ease, color 180ms ease, border-color 180ms ease;
}
.button-primary { background: var(--charcoal); color: var(--white); }
.button-primary:hover { background: var(--sage); }
.button-secondary { border-color: var(--charcoal); color: var(--charcoal); }
.button-secondary:hover { background: var(--charcoal); color: var(--white); }
.button-light { background: var(--off-white); color: var(--charcoal); }
.button-light:hover { background: var(--sage-pale); }
.text-link {
  display: inline-block;
  font-size: 0.92rem;
  font-weight: 700;
  text-decoration-thickness: 1px;
}
.text-link span { display: inline-block; transition: transform 180ms ease; }
.text-link:hover span { transform: translateX(0.25rem); }

:focus-visible {
  outline: 3px solid #a85d17;
  outline-offset: 4px;
}

/* Header */
.site-header {
  position: relative;
  z-index: 50;
  background: rgba(248, 246, 242, 0.98);
  border-bottom: var(--border);
}
.header-inner {
  min-height: 7rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 2rem;
}
.brand { display: inline-flex; align-items: center; gap: 0.9rem; text-decoration: none; }
.brand-mark {
  width: 3.25rem;
  height: 3.25rem;
  display: grid;
  place-items: center;
  background: var(--charcoal);
  color: var(--white);
  border-radius: 50%;
  font-family: var(--font-display);
  font-size: 1.25rem;
  letter-spacing: -0.04em;
}
.brand-copy { display: grid; line-height: 1; }
.brand-name { font-size: 1.15rem; font-weight: 700; letter-spacing: -0.02em; }
.brand-discipline { margin-top: 0.38rem; color: var(--muted); font-size: 0.65rem; font-weight: 700; letter-spacing: 0.25em; text-transform: uppercase; }
.primary-nav { display: flex; align-items: center; gap: clamp(1.2rem, 2.4vw, 2.4rem); }
.primary-nav a { font-size: 0.84rem; font-weight: 700; text-decoration: none; }
.primary-nav a:not(.nav-cta) { padding-block: 0.55rem; border-bottom: 1px solid transparent; }
.primary-nav a:not(.nav-cta):hover,
.primary-nav a[aria-current="page"]:not(.nav-cta) { border-color: var(--charcoal); }
.nav-cta { padding: 0.8rem 1.2rem; background: var(--charcoal); color: var(--white); }
.nav-cta:hover { background: var(--sage); }
.nav-toggle { display: none; border: 0; background: transparent; padding: 0.5rem; }
.demo-bar { background: var(--charcoal); color: var(--white); font-size: 0.78rem; line-height: 1.5; text-align: center; }
.demo-bar .shell { padding-block: 0.7rem; }

/* Shared image treatment */
.image-frame { margin: 0; overflow: hidden; background: var(--stone-pale); }
.image-frame img, .full-bleed-image img { width: 100%; height: 100%; object-fit: cover; }
.image-frame-tall { aspect-ratio: 4 / 5; }
.image-frame-landscape { aspect-ratio: 7 / 5; }
.portrait-frame { aspect-ratio: 4 / 5; }
.portrait-frame-short { aspect-ratio: 5 / 6; }

/* Home hero */
.hero { padding-block: clamp(4.5rem, 8vw, 8rem); }
.hero-grid { display: grid; grid-template-columns: minmax(0, 1.05fr) minmax(360px, 0.82fr); align-items: center; gap: clamp(3rem, 7vw, 8rem); }
.hero-copy { padding-block: 2rem; }
.hero-home h1 { max-width: 8ch; }
.hero-media { max-height: 780px; }

.recognition { border-block: var(--border); }
.recognition-grid { display: grid; grid-template-columns: repeat(3, 1fr); }
.recognition-grid p { margin: 0; padding: 1.45rem 2rem; text-align: center; font-size: 0.8rem; font-weight: 700; letter-spacing: 0.04em; }
.recognition-grid p + p { border-left: var(--border); }
.recognition-grid span { margin-right: 0.6rem; color: var(--sage); }

.section { padding-block: var(--section-space); }
.section-border-top { border-top: var(--border); }
.section-sage { background: var(--sage-pale); }
.section-stone { background: var(--stone-pale); }
.section-dark { background: var(--charcoal-deep); color: var(--off-white); }
.split { display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr); gap: clamp(3rem, 7vw, 8rem); align-items: center; }
.split-wide { grid-template-columns: minmax(0, 0.9fr) minmax(0, 1.1fr); align-items: start; }
.split-wide h2 { max-width: 10ch; }
.split-image { gap: clamp(3rem, 8vw, 9rem); }
.prose { max-width: var(--content); }
.prose > :last-child { margin-bottom: 0; }
.prose h2 { margin-bottom: 2rem; }
.prose-light { color: #e6e8e4; }
.prose-light p { color: #c6cac6; }
.section-heading { max-width: 900px; margin-bottom: clamp(3.5rem, 6vw, 6rem); }
.section-heading-wide { max-width: 1120px; }
.section-heading h2 { max-width: 12ch; }
.section-heading-light h2 { color: var(--off-white); }

.editorial-list, .process-list, .support-grid, .values-grid, .footer-links, .compact-steps { list-style: none; margin: 0; padding: 0; }
.editorial-list { border-top: var(--border); }
.editorial-list li {
  display: grid;
  grid-template-columns: 5rem 1fr;
  gap: 1.5rem;
  padding-block: 2rem;
  border-bottom: var(--border);
}
.editorial-list li > span { color: var(--sage); font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; }
.editorial-list h3 { margin-bottom: 0.5rem; }
.editorial-list p { margin: 0; color: var(--muted); }

.quote-section { border-block: var(--border); }
.quote-grid { display: grid; grid-template-columns: 0.35fr 1fr; gap: 4rem; align-items: start; }
.quote-grid blockquote { margin: 0; padding-left: clamp(1.5rem, 4vw, 4rem); border-left: 2px solid var(--sage); }
.quote-grid blockquote p { margin-bottom: 1.5rem; font-family: var(--font-display); font-size: clamp(2.5rem, 5vw, 5rem); line-height: 1.04; letter-spacing: -0.025em; }
.quote-grid cite { color: var(--muted); font-size: 0.8rem; font-style: normal; font-weight: 700; letter-spacing: 0.1em; text-transform: uppercase; }

.next-step-grid { display: grid; grid-template-columns: minmax(0, 0.95fr) minmax(0, 1fr); gap: clamp(3rem, 8vw, 9rem); align-items: start; }
.next-step-grid h2 { max-width: 10ch; }

/* Inner pages */
.page-hero { padding-block: clamp(5rem, 9vw, 10rem); }
.page-hero-grid { display: grid; grid-template-columns: minmax(0, 1fr) minmax(360px, 0.78fr); gap: clamp(3rem, 8vw, 9rem); align-items: center; }
.page-hero-grid h1 { font-size: clamp(4rem, 7vw, 7.75rem); }
.page-hero-text { min-height: 68vh; display: grid; align-items: center; }
.narrow-hero { max-width: 980px; }
.narrow-hero h1 { max-width: 11ch; }
.align-end { align-items: end; }
.full-bleed-image { width: min(100% - (var(--gutter) * 2), 1600px); height: min(66vw, 850px); margin-inline: auto; overflow: hidden; }
.portrait-wide img { object-position: center 28%; }

.support-grid { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); border-top: var(--border); border-left: var(--border); }
.support-grid li { min-height: 300px; padding: clamp(2rem, 4vw, 4rem); border-right: var(--border); border-bottom: var(--border); }
.support-grid span, .values-grid span { display: block; margin-bottom: 3rem; color: var(--sage); font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; }
.support-grid h2 { font-size: clamp(2rem, 3vw, 3.2rem); max-width: 13ch; }
.support-grid p { margin-bottom: 0; color: var(--muted); }

.process-list { border-top: 1px solid #4d5353; }
.process-list li { display: grid; grid-template-columns: 6rem 1fr; gap: 2rem; padding-block: 2.4rem; border-bottom: 1px solid #4d5353; }
.process-list li > span { color: #9caf9e; font-size: 0.75rem; font-weight: 700; letter-spacing: 0.12em; }
.process-list h3 { color: var(--off-white); }
.process-list p { max-width: 760px; margin-bottom: 0; color: #c4c8c5; }

.practical-grid { display: grid; grid-template-columns: 0.45fr 1fr; gap: clamp(3rem, 8vw, 9rem); }
.practical-intro h2 { max-width: 8ch; }
.definition-grid { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); border-top: var(--border); border-left: var(--border); }
.definition-grid > div { min-height: 180px; padding: 2rem; border-right: var(--border); border-bottom: var(--border); }
.definition-grid dt { margin-bottom: 1.2rem; font-family: var(--font-display); font-size: 1.8rem; line-height: 1.1; }
.definition-grid dd { margin: 0; color: var(--muted); }
.editorial-columns { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: clamp(3rem, 8vw, 9rem); }
.editorial-columns article + article { padding-left: clamp(2rem, 5vw, 5rem); border-left: var(--border); }
.editorial-columns h2 { font-size: clamp(2.5rem, 4vw, 4.2rem); max-width: 10ch; }

.values-grid { display: grid; grid-template-columns: repeat(4, minmax(0, 1fr)); border-top: var(--border); }
.values-grid li { padding: 2rem 2rem 0 0; }
.values-grid li + li { padding-left: 2rem; border-left: var(--border); }
.values-grid p { color: var(--muted); }

/* Contact */
.contact-grid { display: grid; grid-template-columns: minmax(0, 1.1fr) minmax(320px, 0.65fr); gap: clamp(4rem, 9vw, 10rem); align-items: start; }
.contact-form { max-width: 760px; }
.form-field { margin-bottom: 2rem; }
.form-field label { display: block; margin-bottom: 0.65rem; font-size: 0.83rem; font-weight: 700; }
.form-field label span { color: var(--muted); font-weight: 400; }
.form-field input, .form-field select, .form-field textarea {
  width: 100%;
  min-height: 3.4rem;
  border: 0;
  border-bottom: 1px solid var(--charcoal);
  background: transparent;
  color: var(--charcoal);
  padding: 0.6rem 0;
}
.form-field textarea { resize: vertical; }
.form-field select { cursor: pointer; }
.field-note, .demo-note { margin-top: 0.65rem; color: var(--muted); font-size: 0.78rem; }
.consent-field { display: grid; grid-template-columns: 1.25rem 1fr; gap: 0.8rem; align-items: start; margin-block: 2.2rem; font-size: 0.84rem; }
.consent-field input { width: 1.15rem; height: 1.15rem; margin-top: 0.25rem; accent-color: var(--charcoal); }
.honeypot { position: absolute !important; left: -9999px !important; }
.contact-image { aspect-ratio: 4 / 5; margin-bottom: 2.5rem; }
.contact-details { margin: 0; border-top: var(--border); }
.contact-details > div { padding-block: 1.2rem; border-bottom: var(--border); }
.contact-details dt { margin-bottom: 0.25rem; color: var(--sage); font-size: 0.68rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; }
.contact-details dd { margin: 0; }
.compact-steps { border-top: var(--border); }
.compact-steps li { display: grid; grid-template-columns: 4rem 1fr; gap: 1rem; padding-block: 1.5rem; border-bottom: var(--border); }
.compact-steps span { color: var(--sage); font-size: 0.75rem; font-weight: 700; }
.compact-steps p { margin: 0; }

/* Legal */
.legal-content { max-width: 850px; }
.legal-content h2 { margin-top: 4rem; font-size: clamp(2.2rem, 4vw, 3.8rem); }
.legal-content h2:first-child { margin-top: 0; }
.legal-content p { color: var(--muted); }

/* Footer */
.crisis-strip { padding-block: 3.5rem; background: #efe6de; border-top: 1px solid #d8c9bc; }
.crisis-grid { display: grid; grid-template-columns: 0.8fr 1fr; gap: clamp(2rem, 6vw, 6rem); }
.crisis-grid h2 { margin: 0; font-size: clamp(2rem, 3.5vw, 3.8rem); max-width: 12ch; }
.crisis-grid p:last-child { margin: 0; }
.site-footer { padding-top: 5rem; background: var(--charcoal-deep); color: #d9ddda; }
.footer-grid { display: grid; grid-template-columns: 1.5fr repeat(3, 0.65fr); gap: 3rem; padding-bottom: 4rem; }
.brand-footer .brand-mark { background: var(--off-white); color: var(--charcoal); }
.brand-footer .brand-name { color: var(--off-white); }
.brand-footer .brand-discipline { color: #9fa6a1; }
.footer-intro p { max-width: 28rem; margin-top: 1.8rem; color: #aeb4af; }
.footer-heading { margin-bottom: 1.2rem; color: var(--off-white); font-size: 0.72rem; font-weight: 700; letter-spacing: 0.12em; text-transform: uppercase; }
.footer-links li { margin-bottom: 0.55rem; color: #b7bdb8; font-size: 0.88rem; }
.footer-links a { text-decoration: none; }
.footer-links a:hover { color: var(--white); }
.footer-bottom { display: flex; justify-content: space-between; gap: 2rem; padding-block: 1.5rem; border-top: 1px solid #454a49; color: #8e9690; font-size: 0.75rem; }
.footer-bottom p { margin: 0; }

@media (max-width: 1100px) {
  .hero-grid, .page-hero-grid { grid-template-columns: minmax(0, 1fr) minmax(320px, 0.8fr); gap: 3.5rem; }
  .values-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .values-grid li { padding: 2rem; border-bottom: var(--border); }
  .values-grid li:nth-child(odd) { padding-left: 0; border-left: 0; }
  .footer-grid { grid-template-columns: 1.3fr repeat(3, 0.7fr); }
}

@media (max-width: 959px) {
  .header-inner { min-height: 5.5rem; }
  .nav-toggle { display: inline-flex; align-items: center; gap: 0.8rem; z-index: 80; cursor: pointer; }
  .nav-toggle-label { font-size: 0.78rem; font-weight: 700; }
  .nav-toggle-lines { width: 1.5rem; display: grid; gap: 0.4rem; }
  .nav-toggle-lines span { height: 1px; background: currentColor; transition: transform 180ms ease; }
  .nav-open .nav-toggle-lines span:first-child { transform: translateY(0.22rem) rotate(45deg); }
  .nav-open .nav-toggle-lines span:last-child { transform: translateY(-0.22rem) rotate(-45deg); }
  .primary-nav {
    position: fixed;
    inset: 0;
    z-index: 70;
    display: grid;
    align-content: center;
    justify-items: start;
    gap: 1.25rem;
    padding: 7rem var(--gutter) 3rem;
    background: var(--off-white);
    transform: translateX(100%);
    visibility: hidden;
    transition: transform 220ms ease, visibility 220ms ease;
  }
  .nav-open .primary-nav { transform: translateX(0); visibility: visible; }
  .primary-nav a { font-family: var(--font-display); font-size: clamp(2.5rem, 7vw, 4.5rem); font-weight: 400; }
  .primary-nav a:not(.nav-cta) { border: 0; }
  .nav-cta { margin-top: 1rem; font-family: var(--font-body) !important; font-size: 0.9rem !important; font-weight: 700 !important; }

  .hero-grid, .page-hero-grid, .split, .split-wide, .next-step-grid, .contact-grid, .practical-grid, .crisis-grid { grid-template-columns: 1fr; }
  .hero-copy { padding-block: 0; }
  .hero-media { max-height: none; }
  .hero-grid .hero-media { width: min(100%, 680px); }
  .page-hero-grid .image-frame { width: min(100%, 760px); }
  .split-wide h2 { max-width: 12ch; }
  .split-image .image-frame { width: min(100%, 760px); }
  .reverse-mobile .image-frame { grid-row: 1; }
  .recognition-grid { grid-template-columns: 1fr; }
  .recognition-grid p { text-align: left; }
  .recognition-grid p + p { border-left: 0; border-top: var(--border); }
  .quote-grid { grid-template-columns: 1fr; gap: 2rem; }
  .quote-grid blockquote { padding-left: 1.5rem; }
  .support-grid { grid-template-columns: 1fr; }
  .editorial-columns { grid-template-columns: 1fr; }
  .editorial-columns article + article { padding: 3rem 0 0; border-left: 0; border-top: var(--border); }
  .contact-aside { display: grid; grid-template-columns: minmax(220px, 0.65fr) 1fr; gap: 2rem; align-items: start; }
  .contact-image { margin: 0; }
  .footer-grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .footer-intro { grid-column: 1 / -1; }
}

@media (max-width: 640px) {
  :root { --gutter: 1.25rem; --section-space: 4.5rem; }
  body { font-size: 0.96rem; }
  h1 { font-size: clamp(3.5rem, 18vw, 5.4rem); }
  h2 { font-size: clamp(2.7rem, 13vw, 4.2rem); }
  .brand-mark { width: 2.8rem; height: 2.8rem; }
  .brand-name { font-size: 1rem; }
  .brand-discipline { font-size: 0.58rem; }
  .demo-bar { text-align: left; }
  .demo-bar .shell { width: min(100% - 2rem, var(--shell)); }
  .hero, .page-hero { padding-block: 4.5rem; }
  .page-hero-text { min-height: 0; }
  .hero-grid, .page-hero-grid { gap: 2.75rem; }
  .hero-lede, .prose-large { font-size: 1.05rem; }
  .button-row { align-items: stretch; }
  .button-row .button { width: 100%; }
  .full-bleed-image { width: 100%; height: 70vw; min-height: 340px; }
  .editorial-list li, .process-list li { grid-template-columns: 3rem 1fr; gap: 1rem; }
  .support-grid li { min-height: 0; padding: 2rem 1.25rem; }
  .definition-grid { grid-template-columns: 1fr; }
  .values-grid { grid-template-columns: 1fr; }
  .values-grid li, .values-grid li + li { padding: 2rem 0; border-left: 0; border-bottom: var(--border); }
  .contact-aside { grid-template-columns: 1fr; }
  .contact-image { aspect-ratio: 7 / 5; }
  .footer-grid { grid-template-columns: 1fr; }
  .footer-intro { grid-column: auto; }
  .footer-bottom { flex-direction: column; gap: 0.35rem; }
}

@media (prefers-reduced-motion: reduce) {
  html { scroll-behavior: auto; }
  *, *::before, *::after { scroll-behavior: auto !important; transition-duration: 0.01ms !important; animation-duration: 0.01ms !important; animation-iteration-count: 1 !important; }
}

```

## `assets/js/main.js`

```javascript
(() => {
  const toggle = document.querySelector('[data-nav-toggle]');
  const nav = document.querySelector('[data-nav]');

  if (toggle && nav) {
    const closeMenu = () => {
      toggle.setAttribute('aria-expanded', 'false');
      document.body.classList.remove('nav-open');
    };

    toggle.addEventListener('click', () => {
      const isOpen = toggle.getAttribute('aria-expanded') === 'true';
      toggle.setAttribute('aria-expanded', String(!isOpen));
      document.body.classList.toggle('nav-open', !isOpen);
    });

    nav.querySelectorAll('a').forEach((link) => link.addEventListener('click', closeMenu));

    document.addEventListener('keydown', (event) => {
      if (event.key === 'Escape') {
        closeMenu();
        toggle.focus();
      }
    });

    window.addEventListener('resize', () => {
      if (window.innerWidth >= 960) closeMenu();
    });
  }

  document.querySelectorAll('[data-current-year]').forEach((element) => {
    element.textContent = String(new Date().getFullYear());
  });
})();

```

## `index.html`

```html
---
layout: default
title: Counselling in Stockport and online
description: A calm place to slow down, understand what is happening beneath the surface, and find a way forward that feels like your own.
permalink: /
body_class: home
social_image: /assets/images/og-image.webp
---
<section class="hero hero-home">
  <div class="shell hero-grid">
    <div class="hero-copy">
      <p class="eyebrow">Counselling in Stockport and online</p>
      <h1>Space to hear yourself again.</h1>
      <p class="hero-lede">When life feels heavy, tangled or difficult to put into words, counselling offers somewhere to slow down. You do not need to arrive with an explanation. We can begin with what is here.</p>
      <div class="button-row">
        <a class="button button-primary" href="{{ '/contact/' | relative_url }}">Arrange an initial conversation</a>
        <a class="text-link" href="{{ '/how-i-work/' | relative_url }}">See how counselling works <span aria-hidden="true">→</span></a>
      </div>
    </div>
    <figure class="hero-media image-frame image-frame-tall">
      <img src="{{ '/assets/images/hero-room.webp' | relative_url }}" alt="A quiet counselling room with two chairs, natural materials and soft window light" width="1200" height="1500" fetchpriority="high">
    </figure>
  </div>
</section>

<section class="recognition" aria-label="Practice details">
  <div class="shell recognition-grid">
    <p><span>01</span> Adults aged 18+</p>
    <p><span>02</span> Stockport and online</p>
    <p><span>03</span> Weekly 50-minute sessions</p>
  </div>
</section>

<section class="section section-problem" id="support">
  <div class="shell split split-wide">
    <div>
      <p class="eyebrow">When you may be looking for support</p>
      <h2>Perhaps you have been holding things together for a long time.</h2>
    </div>
    <div class="prose prose-large">
      <p>From the outside, life may still look manageable. Inside, you might feel anxious, flat, disconnected, overwhelmed or caught in patterns you understand but cannot seem to change.</p>
      <p>Counselling does not ask you to perform, explain everything quickly or become a different person. It creates room to notice what has been pushed aside and understand yourself with more honesty and less judgement.</p>
      <a class="text-link" href="{{ '/support/' | relative_url }}">Read about the support I offer <span aria-hidden="true">→</span></a>
    </div>
  </div>
</section>

<section class="section section-sage">
  <div class="shell">
    <div class="section-heading section-heading-wide">
      <p class="eyebrow">A relational approach</p>
      <h2>Change can begin when you no longer have to face yourself alone.</h2>
    </div>
    <div class="split split-image">
      <figure class="image-frame image-frame-landscape">
        <img src="{{ '/assets/images/hands-notebook.webp' | relative_url }}" alt="Hands resting beside an open notebook in soft natural light" width="1400" height="1000" loading="lazy">
      </figure>
      <div class="prose prose-large">
        <p>My role is not to diagnose your life from a distance or hand you a formula. I offer a steady, attentive relationship where your experience can be explored at a pace that feels manageable.</p>
        <p>We may look at the feelings, relationships and protective patterns shaping the present. The aim is not a polished version of you. It is a clearer, more compassionate relationship with who you already are.</p>
        <a class="button button-secondary" href="{{ '/how-i-work/' | relative_url }}">How I work</a>
      </div>
    </div>
  </div>
</section>

<section class="section outcomes-section">
  <div class="shell">
    <div class="section-heading">
      <p class="eyebrow">What counselling can make room for</p>
      <h2>Not instant answers. A more honest way forward.</h2>
    </div>
    <ol class="editorial-list">
      <li><span>01</span><div><h3>Understanding</h3><p>Seeing familiar reactions and patterns with greater clarity.</p></div></li>
      <li><span>02</span><div><h3>Self-trust</h3><p>Making decisions with more awareness of your own needs and limits.</p></div></li>
      <li><span>03</span><div><h3>Emotional room</h3><p>Feeling less consumed by what you carry, even when life remains complicated.</p></div></li>
      <li><span>04</span><div><h3>Connection</h3><p>Relating to yourself and other people with less defence and more choice.</p></div></li>
    </ol>
  </div>
</section>

<section class="section section-dark about-preview">
  <div class="shell split split-image reverse-mobile">
    <div class="prose prose-light prose-large">
      <p class="eyebrow eyebrow-light">About Michael</p>
      <h2>A calm, thoughtful presence for work that may not feel simple.</h2>
      <p>I offer counselling with warmth, honesty and care. You will not be rushed towards a conclusion or expected to present a neat version of your experience.</p>
      <p>The relationship matters. I aim to create a space where you can speak freely, pause when you need to, and gradually hear what your own experience has been trying to communicate.</p>
      <a class="button button-light" href="{{ '/about/' | relative_url }}">More about me</a>
    </div>
    <figure class="image-frame portrait-frame">
      <img src="{{ '/assets/images/michael-portrait.webp' | relative_url }}" alt="Michael seated beside a window in a calm, informal portrait" width="1100" height="1400" loading="lazy">
    </figure>
  </div>
</section>

<section class="section quote-section">
  <div class="shell quote-grid">
    <p class="eyebrow">A place to begin</p>
    <blockquote>
      <p>“You do not need to arrive with the right words. We can begin with what is here.”</p>
      <cite>Michael Doe</cite>
    </blockquote>
  </div>
</section>

<section class="section next-step-section">
  <div class="shell next-step-grid">
    <div>
      <p class="eyebrow">Your next step</p>
      <h2>A brief conversation, without pressure.</h2>
    </div>
    <div class="prose prose-large">
      <p>You can send a short message about what brings you here. I will reply with availability and we can arrange a free 20-minute conversation to see whether working together feels right.</p>
      <a class="button button-primary" href="{{ '/contact/' | relative_url }}">Get in touch</a>
    </div>
  </div>
</section>

```

## `support.html`

```html
---
layout: default
title: Support
description: Counselling support for anxiety, low mood, grief, self-criticism, relationship difficulties, identity and periods of change.
permalink: /support/
body_class: inner-page
social_image: /assets/images/support-window.webp
---
<section class="page-hero">
  <div class="shell page-hero-grid">
    <div>
      <p class="eyebrow">Support</p>
      <h1>You do not have to make sense of it alone.</h1>
      <p class="hero-lede">People often begin counselling when the way they have been coping no longer feels sustainable, even if they cannot yet describe exactly what is wrong.</p>
    </div>
    <figure class="image-frame image-frame-landscape">
      <img src="{{ '/assets/images/support-window.webp' | relative_url }}" alt="Soft daylight falling across a quiet window and linen curtain" width="1400" height="1000">
    </figure>
  </div>
</section>

<section class="section section-border-top">
  <div class="shell split split-wide">
    <div>
      <p class="eyebrow">What may be present</p>
      <h2>There is no threshold you have to cross before your experience matters.</h2>
    </div>
    <div class="prose prose-large">
      <p>You may be carrying something recent, something longstanding, or a quieter sense that life has become disconnected from who you are.</p>
      <p>The language below is not a diagnostic checklist. It is simply a way to recognise some of the experiences people bring into counselling.</p>
    </div>
  </div>
</section>

<section class="section section-stone">
  <div class="shell">
    <ul class="support-grid">
      <li><span>01</span><h2>Anxiety and overthinking</h2><p>A mind that rarely settles, persistent worry, dread or the feeling that something is about to go wrong.</p></li>
      <li><span>02</span><h2>Low mood and disconnection</h2><p>Feeling flat, distant from yourself, exhausted by ordinary demands or unable to find meaning in familiar things.</p></li>
      <li><span>03</span><h2>Self-criticism and shame</h2><p>A harsh inner voice, perfectionism, difficulty accepting care or a sense that you are always falling short.</p></li>
      <li><span>04</span><h2>Relationships</h2><p>Repeating patterns of withdrawal, conflict, people-pleasing, mistrust or difficulty expressing what you need.</p></li>
      <li><span>05</span><h2>Grief and loss</h2><p>Living with bereavement, separation, a change in identity or the loss of a future you expected to have.</p></li>
      <li><span>06</span><h2>Change and identity</h2><p>Questioning who you are, adjusting to a new stage of life or trying to live with greater honesty and alignment.</p></li>
    </ul>
  </div>
</section>

<section class="section">
  <div class="shell split split-image">
    <figure class="image-frame image-frame-landscape">
      <img src="{{ '/assets/images/quiet-path.webp' | relative_url }}" alt="A quiet path moving through soft, muted woodland light" width="1400" height="1000" loading="lazy">
    </figure>
    <div class="prose prose-large">
      <p class="eyebrow">How we begin</p>
      <h2>You can start with the part you can name.</h2>
      <p>You do not need a complete history or a clear goal before making contact. The first conversation is simply an opportunity to say a little about what brings you here and ask any practical questions.</p>
      <p>If we decide to work together, the shape of the counselling will emerge through the relationship rather than being imposed in advance.</p>
      <a class="button button-primary" href="{{ '/contact/' | relative_url }}">Arrange an initial conversation</a>
    </div>
  </div>
</section>

```

## `how-i-work.html`

```html
---
layout: default
title: How I work
description: A calm, relational and person-centred approach to counselling, shaped around the individual rather than a fixed formula.
permalink: /how-i-work/
body_class: inner-page
social_image: /assets/images/chairs-detail.webp
---
<section class="page-hero page-hero-text">
  <div class="shell narrow-hero">
    <p class="eyebrow">How I work</p>
    <h1>Counselling that follows the person, not a formula.</h1>
    <p class="hero-lede">My way of working is relational and person-centred. That means your experience, your pace and the quality of the relationship guide the work.</p>
  </div>
</section>

<section class="full-bleed-image">
  <img src="{{ '/assets/images/chairs-detail.webp' | relative_url }}" alt="Two chairs positioned for a private counselling conversation" width="1800" height="1050">
</section>

<section class="section">
  <div class="shell split split-wide">
    <div>
      <p class="eyebrow">The therapeutic relationship</p>
      <h2>A space where you do not have to manage the other person.</h2>
    </div>
    <div class="prose prose-large">
      <p>In everyday life, you may be used to editing yourself, anticipating reactions or taking care of how other people feel. Counselling offers a different kind of relationship.</p>
      <p>I will listen closely, respond honestly and stay curious about the meaning of your experience. I may notice patterns, reflect what I hear or invite us to pause with something that feels important. I will not tell you who to be.</p>
    </div>
  </div>
</section>

<section class="section section-dark">
  <div class="shell">
    <div class="section-heading section-heading-wide section-heading-light">
      <p class="eyebrow eyebrow-light">The process</p>
      <h2>Clear enough to feel safe. Open enough to remain yours.</h2>
    </div>
    <ol class="process-list">
      <li><span>01</span><div><h3>Initial conversation</h3><p>A free 20-minute call to discuss what brings you to counselling, answer questions and check practical fit.</p></div></li>
      <li><span>02</span><div><h3>First session</h3><p>We begin with what feels most present. There is no pressure to tell your whole story at once.</p></div></li>
      <li><span>03</span><div><h3>Ongoing work</h3><p>Weekly sessions create continuity. We review the work together rather than following a hidden plan.</p></div></li>
      <li><span>04</span><div><h3>Ending</h3><p>Endings are discussed openly and planned with care, giving us time to reflect on what has changed.</p></div></li>
    </ol>
  </div>
</section>

<section class="section">
  <div class="shell split split-image reverse-mobile">
    <div class="prose prose-large">
      <p class="eyebrow">What I value</p>
      <h2>Warmth, clarity and respect for your autonomy.</h2>
      <p>I believe people make meaningful changes when they feel safe enough to encounter their experience more fully. The aim is not dependence on therapy. It is a stronger capacity to recognise, trust and respond to your own inner life.</p>
      <p>Good counselling can include silence, uncertainty, humour, emotion and contradiction. Nothing needs to be made tidier than it really is.</p>
    </div>
    <figure class="image-frame portrait-frame-short">
      <img src="{{ '/assets/images/stone-light.webp' | relative_url }}" alt="Soft natural light moving across warm stone and plaster textures" width="1100" height="1300" loading="lazy">
    </figure>
  </div>
</section>

<section class="section section-sage next-step-section">
  <div class="shell next-step-grid">
    <div><p class="eyebrow">Practical details</p><h2>See what the first session involves.</h2></div>
    <div class="prose prose-large"><p>Session length, fees, location, online work and what to expect are set out clearly on the next page.</p><a class="button button-secondary" href="{{ '/first-session/' | relative_url }}">Your first session</a></div>
  </div>
</section>

```

## `fees.html`

```html
---
layout: default
title: Your first session
description: Clear practical information about the first conversation, counselling sessions, fees, location, online work and cancellations.
permalink: /first-session/
body_class: inner-page
social_image: /assets/images/first-session-table.webp
---
<section class="page-hero">
  <div class="shell page-hero-grid">
    <div>
      <p class="eyebrow">Your first session</p>
      <h1>A clear beginning, without needing to have everything worked out.</h1>
      <p class="hero-lede">The first step is a brief conversation. It gives you a chance to ask questions, get a sense of me and decide whether you would like to arrange a full session.</p>
    </div>
    <figure class="image-frame image-frame-landscape">
      <img src="{{ '/assets/images/first-session-table.webp' | relative_url }}" alt="A simple table with water, two glasses and a notebook in a quiet room" width="1400" height="1000">
    </figure>
  </div>
</section>

<section class="section section-border-top">
  <div class="shell practical-grid">
    <div class="practical-intro"><p class="eyebrow">At a glance</p><h2>The practical details.</h2></div>
    <dl class="definition-grid">
      <div><dt>Initial conversation</dt><dd>20 minutes, online or by phone, with no charge.</dd></div>
      <div><dt>Session length</dt><dd>50 minutes.</dd></div>
      <div><dt>Frequency</dt><dd>Usually weekly, at the same time.</dd></div>
      <div><dt>Fee</dt><dd>£55 per session — sample fee for this demo.</dd></div>
      <div><dt>Location</dt><dd>Stockport and secure online video sessions.</dd></div>
      <div><dt>Availability</dt><dd>Daytime and selected early-evening appointments.</dd></div>
    </dl>
  </div>
</section>

<section class="section section-stone">
  <div class="shell split split-wide">
    <div><p class="eyebrow">What happens</p><h2>The first full session is a conversation, not an assessment you can pass or fail.</h2></div>
    <div class="prose prose-large">
      <p>I may ask what has led you to seek counselling now, what support you already have and what you hope might become different. You can share as much or as little as feels possible.</p>
      <p>We will also discuss confidentiality, contact between sessions, cancellations and how we will review the work. You are welcome to ask direct questions about anything that affects your sense of safety or trust.</p>
    </div>
  </div>
</section>

<section class="section">
  <div class="shell editorial-columns">
    <article>
      <p class="eyebrow">Confidentiality</p>
      <h2>Your privacy matters.</h2>
      <p>What you share is treated as confidential, with clearly explained legal and safeguarding limits. These boundaries are discussed before ongoing work begins.</p>
    </article>
    <article>
      <p class="eyebrow">Cancellations</p>
      <h2>Consistency supports the work.</h2>
      <p>This demo uses a 48-hour cancellation policy. Replace it with the therapist’s approved policy and ensure it matches the client agreement.</p>
    </article>
  </div>
</section>

<section class="section section-dark next-step-section">
  <div class="shell next-step-grid">
    <div><p class="eyebrow eyebrow-light">Begin with a message</p><h2>Tell me only what feels useful.</h2></div>
    <div class="prose prose-light prose-large"><p>A few lines are enough. I will reply with current availability and the next practical step.</p><a class="button button-light" href="{{ '/contact/' | relative_url }}">Get in touch</a></div>
  </div>
</section>

```

## `about.html`

```html
---
layout: default
title: About Michael
description: Learn about Michael Doe's calm, thoughtful and relational approach to counselling for adults in Stockport and online.
permalink: /about/
body_class: inner-page
social_image: /assets/images/michael-portrait-wide.webp
---
<section class="page-hero page-hero-about">
  <div class="shell page-hero-grid align-end">
    <div>
      <p class="eyebrow">About Michael</p>
      <h1>A thoughtful relationship can make difficult experience easier to meet.</h1>
    </div>
    <p class="hero-lede">I offer a calm, attentive space for people who may be used to thinking deeply, coping independently or keeping important parts of themselves out of view.</p>
  </div>
</section>

<section class="full-bleed-image portrait-wide">
  <img src="{{ '/assets/images/michael-portrait-wide.webp' | relative_url }}" alt="Michael in a calm counselling space, photographed in natural window light" width="1800" height="1050">
</section>

<section class="section">
  <div class="shell split split-wide">
    <div><p class="eyebrow">My way of being</p><h2>Warm without being vague. Honest without taking over.</h2></div>
    <div class="prose prose-large">
      <p>I am interested in the person beneath the coping strategies: the part of you that may have learned to stay useful, stay quiet, stay in control or keep moving.</p>
      <p>In our sessions, I will not sit behind a professional mask or expect you to do all the emotional work alone. I bring attention, steadiness and a willingness to be affected by what you share while keeping the focus on your experience.</p>
      <p>I value language that feels human rather than clinical. At the same time, I take the boundaries and responsibilities of counselling seriously.</p>
    </div>
  </div>
</section>

<section class="section section-sage">
  <div class="shell">
    <div class="section-heading"><p class="eyebrow">What you can expect</p><h2>The qualities I try to bring into every session.</h2></div>
    <ul class="values-grid">
      <li><span>01</span><h3>Calm</h3><p>Enough steadiness for difficult feelings to be present without being hurried away.</p></li>
      <li><span>02</span><h3>Curiosity</h3><p>Attention to the meaning of your experience rather than assumptions about what it should mean.</p></li>
      <li><span>03</span><h3>Clarity</h3><p>Direct, understandable communication about the relationship, boundaries and process.</p></li>
      <li><span>04</span><h3>Respect</h3><p>Trust in your autonomy, including your right to question, disagree, pause or end the work.</p></li>
    </ul>
  </div>
</section>

<section class="section">
  <div class="shell split split-image">
    <figure class="image-frame image-frame-landscape">
      <img src="{{ '/assets/images/books-plant.webp' | relative_url }}" alt="A small collection of books and a plant in a softly lit counselling room" width="1400" height="1000" loading="lazy">
    </figure>
    <div class="prose prose-large">
      <p class="eyebrow">Professional information</p>
      <h2>Every trust claim must be real and verifiable.</h2>
      <p>This is a demo template, so qualifications have deliberately not been invented. Before launch, replace this paragraph with the therapist’s verified training, professional registration, membership number where appropriate, insurance, supervision arrangements and relevant experience.</p>
      <p>Only include modalities or specialist areas the therapist is genuinely qualified and competent to offer.</p>
    </div>
  </div>
</section>

<section class="section quote-section">
  <div class="shell quote-grid">
    <p class="eyebrow">My belief</p>
    <blockquote><p>“The purpose of counselling is not to make you easier for the world to live with. It is to help you live with greater contact, freedom and choice.”</p><cite>Michael Doe</cite></blockquote>
  </div>
</section>

<section class="section section-dark next-step-section">
  <div class="shell next-step-grid">
    <div><p class="eyebrow eyebrow-light">Working together</p><h2>The relationship needs to feel right to you.</h2></div>
    <div class="prose prose-light prose-large"><p>An initial conversation gives us both a chance to notice whether there is enough ease and trust to begin.</p><a class="button button-light" href="{{ '/contact/' | relative_url }}">Arrange a conversation</a></div>
  </div>
</section>

```

## `contact.html`

```html
---
layout: default
title: Get in touch
description: Contact Michael Doe Counselling to ask a question or arrange a free initial conversation about counselling in Stockport or online.
permalink: /contact/
body_class: inner-page contact-page
social_image: /assets/images/contact-desk.webp
---
<section class="page-hero page-hero-text">
  <div class="shell narrow-hero">
    <p class="eyebrow">Get in touch</p>
    <h1>Begin with a few lines.</h1>
    <p class="hero-lede">You do not need to explain everything. Tell me what brings you here, whether you prefer Stockport or online sessions, and any times you cannot attend.</p>
  </div>
</section>

<section class="section section-border-top contact-section">
  <div class="shell contact-grid">
    <div class="contact-form-wrap">
      <form class="contact-form" action="{{ site.form_endpoint }}" method="post">
        <input type="hidden" name="_subject" value="New counselling enquiry from the website">
        <input type="text" name="_gotcha" class="honeypot" tabindex="-1" autocomplete="off" aria-hidden="true">

        <div class="form-field">
          <label for="name">Name</label>
          <input id="name" name="name" type="text" autocomplete="name" required>
        </div>

        <div class="form-field">
          <label for="email">Email address</label>
          <input id="email" name="email" type="email" autocomplete="email" required>
        </div>

        <div class="form-field">
          <label for="preference">Session preference <span>(optional)</span></label>
          <select id="preference" name="preference">
            <option value="">Choose an option</option>
            <option>Stockport</option>
            <option>Online</option>
            <option>Either</option>
          </select>
        </div>

        <div class="form-field">
          <label for="message">What would you like me to know?</label>
          <textarea id="message" name="message" rows="7" required></textarea>
          <p class="field-note">Please do not use this form for urgent or emergency support.</p>
        </div>

        <label class="consent-field" for="consent">
          <input id="consent" name="consent" type="checkbox" required>
          <span>I understand this message will be used to respond to my enquiry and handled according to the <a href="{{ '/privacy/' | relative_url }}">privacy notice</a>.</span>
        </label>

        <button class="button button-primary" type="submit">Send enquiry</button>
        {% if site.demo %}<p class="demo-note"><strong>Setup required:</strong> replace <code>REPLACE_ME</code> in <code>_config.yml</code> with the live Formspree form ID before publishing.</p>{% endif %}
      </form>
    </div>

    <aside class="contact-aside" aria-label="Contact details">
      <figure class="image-frame contact-image">
        <img src="{{ '/assets/images/contact-desk.webp' | relative_url }}" alt="A quiet desk with a notebook, ceramic cup and soft natural light" width="1000" height="1200">
      </figure>
      <dl class="contact-details">
        <div><dt>Email</dt><dd><a href="mailto:{{ site.email }}">{{ site.email }}</a></dd></div>
        <div><dt>Telephone</dt><dd><a href="tel:+441610000000">{{ site.phone }}</a></dd></div>
        <div><dt>Location</dt><dd>{{ site.location }}<br>Online throughout the UK</dd></div>
        <div><dt>Response time</dt><dd>Usually within two working days.</dd></div>
      </dl>
    </aside>
  </div>
</section>

<section class="section section-stone">
  <div class="shell split split-wide">
    <div><p class="eyebrow">What happens next</p><h2>A simple, transparent process.</h2></div>
    <ol class="compact-steps">
      <li><span>01</span><p>I reply with current availability and answer any immediate questions.</p></li>
      <li><span>02</span><p>We arrange a free 20-minute conversation by phone or online.</p></li>
      <li><span>03</span><p>If the fit feels right, we agree a regular session time and send the working agreement.</p></li>
    </ol>
  </div>
</section>

```

## `privacy.html`

```html
---
layout: default
title: Privacy notice
description: Template privacy information for website visitors and counselling enquiries.
permalink: /privacy/
body_class: legal-page
---
<section class="page-hero page-hero-text">
  <div class="shell narrow-hero">
    <p class="eyebrow">Privacy</p>
    <h1>Privacy notice.</h1>
    <p class="hero-lede">This page is a structured template and must be reviewed against the therapist’s real data handling, professional requirements and legal advice before launch.</p>
  </div>
</section>

<section class="section section-border-top">
  <article class="shell legal-content">
    <h2>Who is responsible for your data</h2>
    <p>Replace this paragraph with the therapist’s full name or registered business name, business address, email address and role as data controller.</p>

    <h2>Information collected through this website</h2>
    <p>The enquiry form collects the information you choose to provide, such as your name, email address, session preference and message. Do not collect information that is not needed to respond safely and appropriately.</p>

    <h2>How information is used</h2>
    <p>Enquiry information should be used only to respond, assess whether the service may be appropriate, arrange an initial conversation and meet professional or legal obligations.</p>

    <h2>Form provider and hosting</h2>
    <p>Insert accurate details of the website host, form processor, email provider and any analytics or cookie services. Link to their privacy information and document any international data transfers.</p>

    <h2>How long information is kept</h2>
    <p>State clear retention periods for enquiries that do not become clients, active client records and financial records. These periods must match the therapist’s professional policy and insurer requirements.</p>

    <h2>Your rights</h2>
    <p>Explain the rights that apply under UK data protection law and how a person can make a request or complaint. Include the appropriate supervisory authority details after legal review.</p>

    <h2>Cookies</h2>
    <p>This template does not install analytics or marketing cookies. If any are added, implement a compliant consent mechanism and update this notice.</p>

    <h2>Last reviewed</h2>
    <p>Replace with the review date and schedule an annual check.</p>
  </article>
</section>

```

## `404.html`

```html
---
layout: default
title: Page not found
permalink: /404.html
body_class: error-page
---
<section class="page-hero page-hero-text">
  <div class="shell narrow-hero">
    <p class="eyebrow">404</p>
    <h1>This page could not be found.</h1>
    <p class="hero-lede">The address may have changed, or the link may be incomplete.</p>
    <a class="button button-primary" href="{{ '/' | relative_url }}">Return home</a>
  </div>
</section>

```

## `robots.txt`

```text
---
layout: null
---
{% if site.demo %}User-agent: *
Disallow: /
{% else %}User-agent: *
Allow: /
Sitemap: {{ '/sitemap.xml' | absolute_url }}
{% endif %}

```

## `CNAME`

```text
alexanderwatsoncounselling.co.uk

```

## `assets/images/favicon.svg`

```xml
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 64 64" role="img" aria-label="MD">
  <rect width="64" height="64" fill="#2F3333"/>
  <text x="32" y="39" text-anchor="middle" font-family="Georgia, serif" font-size="25" fill="#F8F6F2">MD</text>
</svg>

```

## `IMAGE_PROMPTS.md`

```markdown
# Image production plan

The included `.webp` files are lightweight editorial placeholders so the site works immediately. Replace them with final photography using the exact filenames below. Keep the visual system consistent: quiet editorial realism, natural materials, muted colour, soft northern daylight, restrained composition, no stock-counselling clichés, no text, no logos, no fake therapy interaction.

For a real therapist website, use commissioned photographs of the actual therapist and actual room wherever possible. The portrait prompts below are suitable only for this fictional demo.

## Global visual direction

- Palette: off-white `#F8F6F2`, charcoal `#2F3333`, sage `#7A8B7B`, muted grey `#6B6E6E`, warm stone `#D4D1CB`
- References: Kinfolk, Cereal Magazine, Aesop, John Pawson, quiet British residential architecture
- Light: soft overcast window light or late-afternoon natural light; no flash
- Lens language: medium-format realism, 50–80 mm equivalent, natural depth of field
- Finish: gently desaturated, subtle film grain, realistic materials and skin tones
- Avoid: bright white clinical rooms, staged smiles, hands clasped in a therapy cliché, blue corporate colour, dramatic shadows, visible text, logos, candles everywhere, excessive props

## 01 — Homepage hero

**Filename:** `assets/images/hero-room.webp`  
**Crop:** 4:5 portrait  
**Prompt:**

> quiet premium counselling room in a well-designed British period home, two comfortable upholstered chairs angled toward each other, small round oak table with water and two glasses, warm limewash plaster walls, linen curtain, restrained shelving, one healthy plant, soft overcast northern window light, muted off-white charcoal sage and warm-stone palette, editorial interior photography, Kinfolk and Cereal Magazine restraint, John Pawson composition, realistic natural materials, inviting but private, no people, no text, no logo, no staged therapy clichés, medium-format photography, subtle film grain --ar 4:5 --style raw --stylize 75

## 02 — Relational approach / hands and notebook

**Filename:** `assets/images/hands-notebook.webp`  
**Crop:** 7:5 landscape  
**Prompt:**

> close editorial photograph of relaxed adult hands resting naturally beside an open unlined notebook on a warm oak table, ceramic cup and soft linen partially visible, gentle side light from a window, shallow depth of field, muted warm neutrals and sage, human presence without performance, tactile realistic skin and paper, quiet counselling atmosphere, Cereal Magazine editorial photography, no face, no writing visible, no text, no logo, no clinical props --ar 7:5 --style raw --stylize 60

## 03 — Homepage portrait

**Filename:** `assets/images/michael-portrait.webp`  
**Crop:** 4:5 portrait  
**Prompt:**

> fictional male counsellor in his early forties seated naturally beside a window in a calm British counselling room, relaxed open posture, thoughtful approachable expression, understated dark charcoal overshirt over a soft neutral shirt, environmental portrait rather than corporate headshot, subject slightly off-centre with generous negative space, natural skin texture, soft overcast window light, muted off-white sage and warm-stone palette, quiet editorial realism, medium-format portrait photography, no forced smile, no crossed arms, no text, no logo --ar 4:5 --style raw --stylize 50

## 04 — Support page window

**Filename:** `assets/images/support-window.webp`  
**Crop:** 7:5 landscape  
**Prompt:**

> soft daylight passing through a natural linen curtain in a quiet British interior, edge of a warm plaster wall and simple oak window ledge, subtle movement in the fabric, muted off-white sage and warm-stone colours, contemplative editorial still life, minimal composition with generous negative space, realistic material texture, calm and emotionally resonant, no people, no furniture showroom styling, no text, no logo --ar 7:5 --style raw --stylize 80

## 05 — Support page path

**Filename:** `assets/images/quiet-path.webp`  
**Crop:** 7:5 landscape  
**Prompt:**

> narrow quiet woodland path in Greater Manchester under soft overcast light, close and intimate rather than grand landscape, muted moss green earth and warm grey tones, shallow mist between trees, path gently curves out of sight, meditative editorial nature photography, understated metaphor for movement and uncertainty, no people, no dramatic sun rays, no oversaturation, no text, no logo --ar 7:5 --style raw --stylize 55

## 06 — How I work / two chairs

**Filename:** `assets/images/chairs-detail.webp`  
**Crop:** 12:7 wide landscape  
**Prompt:**

> wide editorial photograph of two distinct comfortable chairs arranged for a private counselling conversation, quiet room with limewash plaster, oak floor, wool rug and a single side table, threshold framing and strong simple architectural lines, soft available daylight, calm uncluttered composition, muted charcoal sage off-white and warm stone, realistic British interior, no people, no text, no logo, no therapy clichés, no bright clinical white --ar 12:7 --style raw --stylize 65

## 07 — How I work / stone and light

**Filename:** `assets/images/stone-light.webp`  
**Crop:** 5:6 portrait  
**Prompt:**

> abstract architectural detail of soft northern daylight moving across limewash plaster and pale limestone, quiet junction of wall and shadow, subtle tactile texture, restrained off-white warm-stone and muted grey palette, John Pawson inspired editorial architecture photograph, minimal but warm, no objects, no people, no text, no logo, realistic natural light --ar 5:6 --style raw --stylize 90

## 08 — First session table

**Filename:** `assets/images/first-session-table.webp`  
**Crop:** 7:5 landscape  
**Prompt:**

> simple round oak table prepared for a first counselling session, clear glass carafe and two water glasses, closed natural-paper notebook, two chairs only partially visible, soft window light, warm plaster room, quiet considered styling, muted off-white charcoal sage and warm stone, premium editorial interior photography, realistic and welcoming without being staged, no people, no visible writing, no text, no logo --ar 7:5 --style raw --stylize 55

## 09 — About page wide portrait

**Filename:** `assets/images/michael-portrait-wide.webp`  
**Crop:** 12:7 wide landscape  
**Prompt:**

> fictional male counsellor in his early forties standing naturally in a calm British counselling room, environmental portrait with the room carrying equal visual weight, subject placed in the right third, relaxed thoughtful expression looking slightly away from camera, soft charcoal overshirt, natural skin texture, window light from the left, muted off-white sage warm-stone palette, quiet editorial photography, generous negative space, no corporate pose, no forced smile, no text, no logo --ar 12:7 --style raw --stylize 45

## 10 — About page books and plant

**Filename:** `assets/images/books-plant.webp`  
**Crop:** 7:5 landscape  
**Prompt:**

> restrained shelf detail in a calm counselling room, small stack of unbranded psychology and literature books with blank spines, simple ceramic vessel and healthy green plant, oak and warm plaster, soft side light, shallow depth of field, tactile editorial still life, muted sage off-white charcoal and warm-stone palette, thoughtful but not overly styled, no readable text, no logo --ar 7:5 --style raw --stylize 70

## 11 — Contact page desk

**Filename:** `assets/images/contact-desk.webp`  
**Crop:** 4:5 portrait  
**Prompt:**

> quiet writing desk beside a window in a refined British interior, open blank notebook, black fountain pen, simple ceramic cup, edge of linen curtain, warm oak surface, soft overcast daylight, generous empty space, muted off-white charcoal sage and warm stone, premium editorial still life, realistic natural materials, calm and private, no readable writing, no laptop, no phone, no text, no logo --ar 4:5 --style raw --stylize 65

## 12 — Social sharing image

**Filename:** `assets/images/og-image.webp`  
**Crop:** 1200 × 630 / 40:21  
**Prompt:**

> wide quiet counselling room detail with two chairs, linen curtain and warm plaster, strong simple composition with clear negative space on the left for optional brand typography added later in Canva, muted off-white charcoal sage and warm stone, editorial British interior photography, natural overcast window light, realistic materials, calm premium atmosphere, no people, no text generated in image, no logo --ar 40:21 --style raw --stylize 60

## Export settings

1. Upscale and lightly edit the selected image before export.
2. Crop to the aspect ratio above before placing it in the site.
3. Export as WebP at roughly 80–88% quality.
4. Keep hero images around 1600–2200 px on the longest edge; supporting images around 1200–1800 px.
5. Preserve the filenames exactly so no HTML changes are required.
6. Confirm each alt description still matches the final image; update the HTML when it does not.

```

## `README.md`

```markdown
# Michael Doe Counselling — premium Jekyll template

A complete, responsive therapist website designed for GitHub Pages/Jekyll. It follows the uploaded website framework: editorial rather than marketing-led, one purpose per page, low-pressure calls to action, strong accessibility, calm typography and a restrained photography system.

## Included pages

- Home — `/`
- Support — `/support/`
- How I work — `/how-i-work/`
- Your first session — `/first-session/`
- About — `/about/`
- Contact — `/contact/`
- Privacy template — `/privacy/`
- 404 page

## Existing repository files to replace

Replace the current files shown in the repository with the files in this package. Add the new `support.html`, `privacy.html`, `404.html`, `assets/js/main.js` and all image files.

## Before launch

1. Replace all fictional demo copy and verify every professional claim.
2. Change `demo: true` to `demo: false` in `_config.yml`.
3. Replace the sample practice name, contact details, location, fees and availability.
4. Replace `REPLACE_ME` in the Formspree endpoint with the live form ID.
5. Replace the generated placeholder images using `IMAGE_PROMPTS.md` or real commissioned photography.
6. Insert verified qualifications, professional registration, memberships, insurance and supervision details.
7. Have the privacy notice and client-facing policies professionally reviewed.
8. Confirm crisis information is appropriate for the practice location and audience.
9. Update `CNAME` and the `url` setting when using another domain.
10. Test keyboard navigation, screen reader output, form handling, mobile layout and page speed before publishing.

## Local preview

This is a Jekyll site. With Ruby and Bundler installed:

```bash
gem install bundler jekyll
jekyll serve
```

Then open `http://localhost:4000`.

## Fonts

- Display: Instrument Serif via Google Fonts
- Body: Manrope via Google Fonts

The uploaded design system specifies Instrument Serif and Aileron. Manrope is used as an accessible webfont substitute until a licensed Aileron webfont is supplied. To use Aileron, self-host the licensed files and change `--font-body` in `assets/css/main.css`.

## File map

```text
/
├── _config.yml
├── _includes/
│   ├── head.html
│   ├── header.html
│   └── footer.html
├── _layouts/
│   └── default.html
├── assets/
│   ├── css/main.css
│   ├── js/main.js
│   └── images/
├── index.html
├── support.html
├── how-i-work.html
├── fees.html
├── about.html
├── contact.html
├── privacy.html
├── 404.html
├── robots.txt
├── CNAME
├── IMAGE_PROMPTS.md
└── FULL_CODE.md
```

```
