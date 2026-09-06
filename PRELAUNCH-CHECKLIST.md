# Pre-launch checklist

Everything on this site that is still a placeholder, plus the client material
that has arrived but is not yet wired in. Grep for `TODO:CLIENT` to find items
in place.

**The site must not go live with any box below unticked.**

---

## BLOCKERS

- [ ] **The site uses one colour outside the official palette.** The italic
      emphasis in every headline is the pre-rebrand gold `#C8A24A`, added on the
      client's explicit instruction because Soft Cream disappears on White and
      on the Soft Cream band. The guidelines say *"Do not use colors that are
      not included in the brand's official palette for brand representation."*
      Measured: **3.7:1 on Deep Blue** (passes AA for large text), **2.4:1 on
      White** and **2.0:1 on Soft Cream** (both below the 3:1 threshold).
      Get this signed off, or switch `--color-gold` to `#a9822f`, which clears
      3:1 on White and still reads as the same gold. One-line change in
      `src/input.css`.

- [ ] **Brand font files.** The guidelines specify **Dream Avenue** (headers)
      and **ITC Avant Garde** (body, Regular + Bold). Neither was in the brand
      bundle and both are licensed commercial faces. The site currently ships
      **Playfair Display** and **Poppins** as documented stand-ins, so it is
      **not yet strictly compliant on typography.**
      Fix: obtain the licensed webfonts, drop the `.woff2` files into
      `public/assets/fonts/`, and update the two `@font-face` blocks and the
      `--font-display` / `--font-sans` tokens in `src/input.css`.

- [ ] **Gallery does not exist.** It is linked from the nav, the footer and the
      home page's "See the full gallery" button, so **those links are 404s.**
      About Us, FAQs, the Enquiry Form and Thank You are built.

      The Process and Testimonials are no longer pages: both nav items are now
      fragment links to sections of the home page (`/#process`,
      `/#testimonials`). The full five-step process also lives on `/about`.

- [ ] **Confirm the enquiry form after the first deploy.** Netlify only
      registers a form when it finds it in the deployed HTML, so it cannot be
      tested locally. After the first deploy: submit the form once, confirm the
      submission appears under **Site configuration → Forms**, confirm the
      couple lands on `/thank-you`, and set up the email notification so an
      enquiry is not sitting unread in the Netlify dashboard.

- [ ] **Mechanical corrections were made to the testimonials.** Words unchanged;
      confirm the client is happy with these:
      - Hema Gowri: `photos-they captured feelings` -> em dash
      - Shanmuga Raja: `Exceeded all expectations! possesses an innate talent`
        -> capital P after the full stop
      - Trailing full stops after the names dropped (`- Thiviia.` -> `Thiviia`)
      - Straight quotes and `...` set as typographic apostrophes and ellipses

- [ ] **Niveditha's review is a raw paste.** It runs to roughly 200 words of
      clauses joined by ellipses, against 50-100 for the others, and is nearly
      twice the height of any other card. Shipped in full and unedited; worth
      asking whether they want it tightened.

- [ ] **A typo in the FAQ copy was corrected.** Q2 read "The invßestment can
      depend on..."; shipped as "investment". Worth confirming with the client
      that no other stray characters survived their draft.

- [ ] **`/faq` publishes a price.** Q2 states "The starting investment price is
      70,000 INR per day." Confirm the client is happy for that figure to be
      public before launch, and that it is current.

- [ ] **Two of the client's process steps have nearly the same name.**
      Step 03 is *"You're Booked"* and step 04 is *"You're On Board"*, but
      step 03's own text also ends "you're officially on board". Reproduced
      verbatim on `/about`; worth asking the client whether 04 should be
      renamed (something like *"On the Day"*).

---

## Client material received but not yet used

The bundle at `TMC Website Bundle - Shared by Narayan/` contains real content
that is still sitting behind Lorem Ipsum on the site:

- [x] ~~`Documents/About Us for TMC Website.docx`~~ — **done.** The full essay
      and all five process steps are live on `/about`, verbatim.
- [x] ~~`Documents/FAQ for TMC.docx`~~ — **done.** All twelve questions and
      answers are live on `/faq`, verbatim.
- [x] ~~`Documents/Testimonials for TMC.docx`~~ — **done.** All nine reviews are
      live on the home page via `partials/testimonials.html`, ready to include
      on each gallery page too.
- [x] ~~`Documents/Enquiry Form for TMC.docx`~~ — **done.** All eleven questions
      are live on `/contact`, wired to Netlify Forms.
- [ ] **120 real photographs** in `Test Assets - Shared by Narayan/`
      (`Highres/` and `Lowres/`). Every image on the site is still Western stock.

Copy that can be lifted straight from the brand guidelines PDF:

- [x] ~~**Philosophy** (p2)~~ — live on `/about`.
- [x] ~~**The idea behind TMC** (p3)~~ — live on `/about`.
- [x] ~~**Who we are** (p4)~~ — live on `/about`.
- [x] ~~Positioning line: *"A place for memories to endure."*~~ — closes `/about`.

Copy that is still ours, not the client's, and needs their approval:

- [ ] `/about` — the Our Process section heading ("Our process, from first
      message to final delivery"). The five steps under it are theirs.
- [ ] `/faq` — the page headline ("The questions couples ask us most") and the
      closing section ("Still have a question? / Ask us anything"). Every
      question and answer is theirs.
- [ ] Testimonials section heading ("In their own words"). The nine reviews
      are theirs.
- [ ] `/index` — the hero headline, all Selected Work captions and the
      three-step process teaser. Still Lorem Ipsum in places. (The placeholder
      testimonial is gone — replaced by the client's real reviews.)
- [ ] `partials/footer.html` — the footer blurb is still Lorem Ipsum.

---

## Imagery

The guidelines are specific: *"Quietly cinematic, intimate, and timeless.
Natural light, soft shadows, muted earthy tones, and subtle film-like grain…
observed rather than staged."* The reference images are South Indian Tamil
weddings — garlands, silks, temple settings.

- [ ] **All current imagery is Western stock and does not match this.** Replace
      with the client's own work throughout:
      `public/assets/img/hero/` (6), `public/assets/img/gallery/` (15 tiles),
      `public/assets/img/work/` (7), `public/assets/img/about/` (2).
- [ ] Re-check each gallery tile's `--focal` crop centre after swapping, or
      square-cropping will cut off faces.
- [ ] Update every `alt` attribute to describe the real photograph.
- [ ] Re-check the hero tint after the swap. `tintOpacity` and `veilOpacity` in
      `preferences.js` were eased to 0.22 / 0.16 because Deep Blue is a mid-tone
      and colourises rather than darkens; the right values depend on the real
      photographs.
- [ ] The About spread renders its two images black & white. Confirm that is
      wanted, or remove the `filter` on `.about__figure img`.

## Copy

- [ ] Hero lede, About body and signature, four "selected work" captions,
      three process steps, testimonial quote, closing CTA, footer positioning line
- [ ] Photographer's name — currently "Placeholder Name, Founder"
- [ ] Statistics "200+ / 12 / 9" are invented

## Still to do

- [ ] **Open Graph image** — still points at a stock hero photo
- [ ] **Instagram** and other social links — currently `href="#"`
- [ ] Real `404.html`
- [ ] Contact form — Netlify Forms needs `data-netlify="true"`, a hidden
      `form-name` input, a honeypot, and a `thank-you.html`
- [ ] Confirm Netlify's current form-submission limit; spam counts toward it
- [ ] Full footer (the current one is provisional)

---

## Done

- [x] Official four-colour palette applied site-wide; no non-palette colour
      remains in the stylesheet
- [x] Official logo artwork in header and footer; tagline lockup in the footer
- [x] Favicon and touch icon generated from the TMC monogram on Deep Blue
- [x] Real contact details: thememoryconservatory@gmail.com, +91 84385 33169,
      #28 Duraiswamy Pillai St, West Tambaram, Chennai
- [x] WhatsApp button wired to the real number
- [x] Contrast audited — 18/18 text styles pass WCAG AA
