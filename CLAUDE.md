# Jaxkey Properties: project context

## Who's who
- **PrimeReach Digital** (primereachmktg.com) is the marketing agency that owns this project. The owner is the person you're working with.
- **Jaxkey Properties** is the client: a real estate investor.
- **The name is spelled "Jaxkey".** The key in the logo stands in for the K. Never write "Jaxey".
- **What Jaxkey buys:** pre-foreclosures, probates, vacant, abandoned and condemned homes, and as-is homes in any condition.
- **What Jaxkey does after buying:** fix and flips, rentals, and owner financing on select homes.
- **Preview link:** https://claude.ai/artifact/9yjYDBAgMysH7ah7Qtz4pg. It mirrors `index.html` as an artifact fragment (no `<html>`, `<head>` or `<body>` tags).

## Hard rules
- **Never invent facts.** That means no testimonials, customer or deal counts, awards, certifications, years in business, service areas, phone numbers or emails. Use only what the owner provides.
- **No "cash offer" wording** until the owner confirms Jaxkey pays cash. It was removed for that reason.
- **No filler images.** No stock photos, no AI-generated house photos, and no illustrative drawings. The owner removed the drawings because they made the site look incomplete. Add images only when they are real Jaxkey project photos.
- **No placeholder text or dead buttons.** Every link must go somewhere and every button must do something.
- **The form must never claim it sent something it didn't.**
- **Copy tone:** calm, plain and respectful. Sellers are often under stress. Avoid "WE BUY HOUSES CASH!!" energy. No em dashes in social captions.

## Design system
- **Palette:** warm ivory, espresso and a little muted gold. Blue (`#1B5FE6`) is kept to a minimum: the logo, the "Get an offer" button in the header, and keyboard focus rings. The owner asked for less blue, so don't add it back.
  - Light: page `#F3EFE7`, paper `#FAF8F3`, stone `#E6DFD0`, ink `#1E1A16`, slate `#5E564B`, dark panel `#2A251F`, header and footer `#12100D`.
  - Muted gold: `--accent` `#A88A5A` for rules and markers, and `--accent-text` `#7D6238` for small text. It's used only on the hero kicker's circle marker, the situation numbers, the "How it works" step numbers and the form confirmation's left border. Keep it that sparse, and don't put `--accent-text` on stone because the contrast is too low.
  - Dark mode is handled with `prefers-color-scheme` and a `data-theme` attribute. All colors are CSS variables in `:root`.
- **Type:** Newsreader (serif headlines), IBM Plex Sans (body text), IBM Plex Mono (small footer text only). All three load from Google Fonts.
- **Shapes:** square 2px corners, thin rules, no shadows, no gradients, no pill-shaped buttons.
- **The logo** is designed for a dark background, so it only appears on the black header and footer.
- **Breakpoints:** 1100, 960 (grid collapses to one column), 900 (the selling / buying band stacks), 860 (menu button replaces the nav), 640 and 560. Tested down to 320px with no horizontal scroll.

## Page structure
1. Sticky header: logo, nav links, "Get an offer." On mobile, a Menu button opens a drawer (closes with Escape).
2. Hero: "Every house has a next chapter." with the lede, calls to action, and three facts.
3. `#what-we-buy`: nine situations in three groups. Each item has the anchor `#s-<key>`, used by the footer links.
4. `#buying`: split band with "Selling a house" (stone) and "Buying or renting" (dark espresso panel).
5. `#offer`: validated form plus the "How it works" steps (`#how`).
   - Links with `data-intent` preselect the form's situation.
   - The "buying" and "owner-financing" situations turn the address field into an optional "Where are you looking?"
6. Footer.

## Open items
- [ ] Get Jaxkey's email and phone, and fill in `const SITE` in `index.html`.
- [ ] After launch, send one test inquiry and click FormSubmit's activation email.
- [ ] Turn on GitHub Pages and connect Jaxkey's domain.
- [ ] Get real project photos (before, during and after, taken from the same spot) for a future "Recent work" section.
- [ ] Confirm whether Jaxkey pays cash.
- [ ] Hero redesign, on hold until Jaxkey has a real photo. The owner picked a Dribbble reference ("Hero Section for a Real Estate Investment Company" by AbdulQudus): a full-width photo on top with the name and nav over it, a small curved tab in the photo's bottom-left corner holding a circle marker and short label, and a beige band below with a large headline on the left and the lede and one button on the right. Keep the seller-first copy; the owner decided against luxury or investor positioning. Don't use a stock or AI photo to fill the slot.
