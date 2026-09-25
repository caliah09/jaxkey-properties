# Jaxkey Properties: project context

## Who's who
- **PrimeReach Digital** (primereachmktg.com) is the marketing agency that owns this project. The owner is the person you're working with.
- **Jaxkey Properties** is the client: a real estate investor.
- **Jaxkey Properties is the owner's family business.** The owner's dad runs it.
- **The owner's dad is also a licensed real estate agent at Linda Blue.** His agent work is separate from Jaxkey. The site must never use Linda Blue's name, logo or branding.
- **License disclosure:** because he's licensed and Jaxkey buys directly from sellers, the site needs a license disclosure. The exact wording is pending his broker's approval. Never write, draft or guess that wording. It goes into `SITE.disclosure` word for word once the owner provides it.
- **Possible future offer:** "sell as-is to Jaxkey, or list it with a licensed agent." Publish it only after his broker approves the wording.
- **The name is spelled "Jaxkey".** The key in the logo stands in for the K. Never write "Jaxey".
- **What Jaxkey buys:** pre-foreclosures, probates, vacant, abandoned and condemned homes, and as-is homes in any condition.
- **What Jaxkey does after buying:** fix and flips, rentals, and owner financing on select homes.
- **Preview link:** https://claude.ai/artifact/9yjYDBAgMysH7ah7Qtz4pg. It mirrors `index.html` as an artifact fragment (no `<html>`, `<head>` or `<body>` tags). Publish `logo.webp`, `favicon.svg` and `apple-touch-icon.png` with it as supporting files.

## Hard rules
- **Never invent facts.** That means no testimonials, customer or deal counts, awards, certifications, years in business, service areas, phone numbers, emails or license wording. Use only what the owner provides.
- **No "cash offer" wording** until the owner confirms Jaxkey pays cash. It was removed for that reason.
- **No filler images.** No stock photos, no AI-generated house photos, and no illustrative drawings. The owner removed the drawings because they made the site look incomplete. Add images only when they are real Jaxkey project photos.
- **No placeholder text or dead buttons.** Every link must go somewhere and every button must do something. Anything that depends on an empty `SITE` field renders nothing until it's filled.
- **The form must never claim it sent something it didn't.**
- **Copy tone:** calm, plain and respectful. Sellers are often under stress. Avoid "WE BUY HOUSES CASH!!" energy. No em dashes in social captions.

## Settings (`const SITE` in `index.html`)
- `formEndpoint`: the Formspree form (`https://formspree.io/f/xkjgzkpb`). Inquiries are sent there as JSON, and Formspree emails them to the address set in its dashboard. If it's blank, the form validates but says plainly that nothing was sent.
- `email` and `phone`: Jaxkey's contact details, shown under "What happens next" and in the footer. `phone` also adds a Call button to the mobile bar.
- `ownerName`: stored for later, not shown on the page yet.
- `disclosure`: the broker-approved license disclosure, shown under the form's button and in the footer above the copyright.
- On load, the page logs a `console.warn` listing any empty fields. The LocalBusiness JSON-LD includes only the fields that have values.

## Design system
- **Palette:** warm ivory, espresso and a little muted gold. Blue (`#1B5FE6`) is kept to a minimum: the logo, the "Get an offer" button in the header, and keyboard focus rings. The owner asked for less blue, so don't add it back.
  - Light: page `#F3EFE7`, paper `#FAF8F3`, stone `#E6DFD0`, ink `#1E1A16`, slate `#5E564B`, dark panel `#2A251F`, header and footer `#12100D`.
  - Muted gold: `--accent` `#A88A5A` for rules and markers, and `--accent-text` `#7D6238` for small text. Right now it appears only on the form confirmation's left border. Keep it that sparse, and don't put `--accent-text` on stone because the contrast is too low.
  - Dark mode is solid black, and the owner chose that on purpose. The header, every section and the footer are all `#000000` with no bands or dividing lines, so the page flows as one surface. The header's bottom line appears only once it compacts on scroll. Text is `#EEE8DE`, secondary text `#B2A898`, and form fields `#0E0D0C`. The `--band`, `--band-rule` and `--header-rule` variables are what switch between light mode's bands and dark mode's flow.
  - Light mode keeps the ivory design, including the paper band behind "Houses we buy" and the dark "Looking for a home?" panel.
  - Themes are handled with `prefers-color-scheme` and a `data-theme` attribute. All colors are CSS variables in `:root`. A footer button cycles Auto / Light / Dark and saves the choice in `localStorage`.
- **Type:** Newsreader (serif headlines, optical sizing on) and IBM Plex Sans (everything else), both from Google Fonts. Headlines use `text-wrap: balance`, paragraphs `text-wrap: pretty`, and paragraphs stay under about 62ch. Use curly quotes and apostrophes.
- **Shapes:** square 2px corners, thin rules, no shadows, no gradients, no pill-shaped buttons.
- **Motion:** quiet and quick. Use only `--ease`, `--dur-fast` (180ms) and `--dur` (420ms).
  - The hero fades up on load, finishing within 700ms.
  - Headings and rows marked `data-reveal` fade up once on scroll. They're hidden only under the `.js` class, which is added only when IntersectionObserver exists, so content stays visible without JS.
  - The header shrinks with transforms after 24px of scroll.
  - The primary button fills left to right on hover, and text-link underlines draw in from the left.
  - `:active` moves 1px down. Never scale, lift or add shadows.
  - `prefers-reduced-motion` turns all of it off.
- **The logo** is `logo.webp` (made from `logo.png`, which stays as the source). It's designed for a dark background, so it only appears on the black header and footer. The favicon is a simple house-and-window mark (`favicon.svg`, plus `apple-touch-icon.png`). A true key-mark favicon needs the original layered logo file.
- **Tap targets** are at least 44px.
- **JavaScript** is vanilla. Keep additions small; the last pass added about 4KB.
- **Breakpoints:** 1100, 960 (the form and "What happens next" stack), 860 (menu button replaces the nav), 640 (the "Houses we buy" rows stack, "Start here" is always visible, and the mobile bar turns on) and 560. Tested at 320, 375, 768, 1024 and 1440px in both themes with no horizontal scroll.
- **Avoid the AI-template look.** The owner said an earlier version looked like an AI template, so it was cut down on purpose. Don't bring back taglines, small labels above headlines, rows of three facts, numbered 01/02/03 items, spec tables or three-step sections. Write plain, specific sentences. The site will feel real once it has Jaxkey's real details (owner's name and photo, service area, real houses), so prefer adding those over adding design.

## Page structure
1. Sticky header: logo, nav links (the one for the section in view is underlined), "Get an offer." On mobile, a Menu button opens a drawer that traps focus and closes with Escape.
2. Hero: "We buy houses in any condition." with one plain paragraph, the main button, and a link to the buying section.
3. `#what-we-buy`, "Houses we buy": six situations as plain rows (name, one sentence). Each row has the anchor `#s-<key>`, and the whole row is a link to `#offer` with a matching `data-intent`. After the jump, the first empty field gets focus and the situation select briefly shows an outline.
4. `#buying`, "Looking for a home?": a dark panel in light mode (plain black in dark mode) with one paragraph, three items (`#s-fixflip`, `#s-rentals`, `#s-ownerfinancing`) and an "Ask what's available" link.
5. `#offer`: the form, split into "About the house" and "How to reach you", plus a short "What happens next" paragraph (`#how`).
   - Links with `data-intent` preselect the form's situation.
   - The "buying" and "owner-financing" situations turn the address field into an optional "Where are you looking?"
   - Valid fields get a small ink checkmark once you leave them. Errors keep their original timing: they appear after the first submit attempt.
   - The swap from form to confirmation uses a view transition when the browser supports it.
6. Footer: logo, nav links, contact details and disclosure once they're filled in, copyright, theme button, and back to top.
7. Mobile bar (640px and below): "Tell us about your house →" appears once the hero button scrolls away and hides while the form is in view.

## Open items
- [ ] Get Jaxkey's email and phone, and fill in `SITE.email` and `SITE.phone`.
- [ ] Get broker-approved license disclosure wording and fill in `SITE.disclosure`.
- [ ] Don't launch or run ads until `SITE.email`, `SITE.phone` and `SITE.disclosure` are filled.
- [ ] After launch, send one real test inquiry and confirm it arrives from Formspree. Check that Formspree accepts submissions from the site's domain.
- [ ] Get the owner's name for `SITE.ownerName`.
- [ ] Turn on GitHub Pages and connect Jaxkey's domain.
- [ ] Get real project photos (before, during and after, taken from the same spot) for a future "Recent work" section.
- [ ] Confirm whether Jaxkey pays cash.
- [ ] Get the original layered logo file, to make a proper key-mark favicon.
- [ ] Hero redesign, on hold until Jaxkey has a real photo. The owner picked a Dribbble reference ("Hero Section for a Real Estate Investment Company" by AbdulQudus): a full-width photo on top with the name and nav over it, a small curved tab in the photo's bottom-left corner holding a circle marker and short label, and a beige band below with a large headline on the left and the lede and one button on the right. Keep the seller-first copy; the owner decided against luxury or investor positioning. Don't use a stock or AI photo to fill the slot.
