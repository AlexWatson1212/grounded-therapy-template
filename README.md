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
