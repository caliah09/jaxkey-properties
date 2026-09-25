# Jaxkey Properties website

A single-page site for Jaxkey Properties, a real estate investor that buys houses in any condition, including pre-foreclosures, probates, and vacant, abandoned or condemned homes. It also sells and rents out the homes it renovates, with owner financing on select homes.

Built and managed by PrimeReach Digital.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site: HTML, CSS and JavaScript in one file. |
| `logo.webp` | The logo the site shows. |
| `logo.png` | The original logo with a transparent background, kept as the source file. |
| `favicon.svg` | Browser tab icon. |
| `apple-touch-icon.png` | Home-screen icon for iPhones. |
| `CLAUDE.md` | Client context and design rules for anyone (or any Claude session) working on the site. |

Upload all of these together; the page loads the images from the same folder.

## Before launch: fill in the settings

Open `index.html` and search for `const SITE`:

```js
const SITE = {
  formEndpoint: 'https://formspree.io/f/xkjgzkpb',
  email: '',
  phone: '',
  ownerName: '',
  disclosure: ''
};
```

- **formEndpoint**: the inquiry form sends to this [Formspree](https://formspree.io) form, which emails each inquiry to the address set up in the Formspree dashboard. Send one test inquiry after launch and make sure it arrives.
- **email**: Jaxkey's contact email, shown on the page.
- **phone**: shown as a tap-to-call link, and as a Call button on phones.
- **ownerName**: stored for later. It isn't shown on the page yet.
- **disclosure**: the license disclosure, pasted exactly as the broker approved it. Shown under the form's button and in the footer.

Any field left blank stays hidden, and the browser console lists the empty ones. If `formEndpoint` is blank, the form still checks the fields but tells the visitor plainly that nothing was sent.

**Don't launch or run ads until `email`, `phone` and `disclosure` are filled in.**

## Hosting on GitHub Pages

1. Go to **Settings → Pages** in this repo.
2. Under **Source**, choose **Deploy from a branch**, then pick `main` and `/ (root)`.
3. The site goes live at `https://caliah09.github.io/jaxkey-properties/` within a minute or two.
4. To use Jaxkey's own domain, enter it under **Custom domain** and add the DNS records GitHub lists.
