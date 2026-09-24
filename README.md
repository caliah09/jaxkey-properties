# Jaxkey Properties website

A single-page site for Jaxkey Properties, a real estate investor that buys houses in any condition, including pre-foreclosures, probates, and vacant, abandoned or condemned homes. It also sells and rents out the homes it renovates, with owner financing on select homes.

Built and managed by PrimeReach Digital.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole site. HTML, CSS and JavaScript in one file. The logo is embedded, so nothing else needs to be uploaded. |
| `logo.png` | The Jaxkey logo with a transparent background, kept here as a source file. |
| `CLAUDE.md` | Client context and design rules for anyone (or any Claude session) working on the site. |

## Before launch: fill in two settings

Open `index.html` and search for `const SITE`:

```js
const SITE = {
  email: '',   // where form inquiries are sent
  phone: ''    // shown under "How it works" and in the footer
};
```

- **email**: the inquiry form sends through [FormSubmit](https://formsubmit.co). It's free and needs no account. The first inquiry triggers a one-time "activate" email to this address; click the link once, and every inquiry after that arrives as a table.
- **phone**: shown as a tap-to-call link. Leave it blank and that line stays hidden.

While `email` is blank, the form still validates the fields, but it tells the visitor plainly that the details were not sent.

## Hosting on GitHub Pages

1. Go to **Settings → Pages** in this repo.
2. Under **Source**, choose **Deploy from a branch**, then pick `main` and `/ (root)`.
3. The site goes live at `https://caliah09.github.io/jaxkey-properties/` within a minute or two.
4. To use Jaxkey's own domain, enter it under **Custom domain** and add the DNS records GitHub lists.
