# Renee Speaks — author site

One page, Bootstrap 5 + custom CSS. No build step, nothing to install.

`index.html` is fully self-contained — all three covers and your author photo
are embedded in the file, and the trailers stream from YouTube. It renders
correctly wherever you open it.

The `assets` folder holds one thing: `og-image.jpg`, the picture that shows
when someone shares your link. Upload it alongside `index.html`.

---

## Everything you'll edit is in one place

Open `index.html`, scroll to the bottom, find `const SITE = {`.

| Setting | What it does |
|---|---|
| `releaseDate` | Drives the countdown. It flips itself to "Available now on Amazon" when the moment passes. |
| `buyUrl` | The Amazon product page for *Pleasure & Pain*. Blank = every buy button falls back to your author page. |
| `trailers` | Each entry's `youtubeId` is the code after `youtube.com/shorts/` — drop anything after the `?`. |
| `socials` | Icons render in the footer. Any you leave blank simply don't appear. |
| `newsletterEndpoint` | Only matters once you switch the signup section back on. |

The **About the Author** text is plain HTML in the `#about` section, marked with
`REPLACE THIS` comments.

## Still to do

1. **Your Amazon bio** into the About section.
2. **`buyUrl`** once the Amazon listing is live.
3. **Your domain** — search the `<head>` for `reneespeaksauthor.com` and swap in
   the real one. Those URLs control how the site looks when shared.
4. **Social links**, whenever you want them in the footer.

## Turning the newsletter back on

The signup section is commented out, not deleted. In `index.html`:

1. Find `SIGNUP — parked` and delete the comment opener and its closer.
2. Inside that block, change `<!~~` back to `<!--` and `~~>` back to `-->`
   (they were swapped so the comment wouldn't terminate early).
3. Un-comment `<a href="#signup">Newsletter</a>` in the nav.
4. Set `SITE.newsletterEndpoint` to the form action URL from your email service.

Until step 4 is done the form politely declines rather than silently losing
addresses.

## Swapping a trailer to a self-hosted file

If you ever want a video off YouTube, replace that entry's
`youtubeId:"..."` with `src:"assets/video/name.mp4"` and put the file there.
Add `wide:true` for a 16:9 trailer; Shorts-shaped vertical is the default.

## Deploying

Drag the folder onto **Netlify Drop** (netlify.com/drop) or **Cloudflare Pages** —
free, HTTPS included, custom domain in a couple of clicks. Whichever registrar
you buy the domain from, turn on **WHOIS privacy** so the registration isn't
publicly searchable under your name.

## Notes

- Responsive throughout; the nav collapses to a menu below 992px.
- Respects `prefers-reduced-motion` — the petals stop for anyone with motion
  reduction enabled at the OS level.
- Keyboard-navigable, visible focus rings, skip link, alt text on every image.
- Trailers embed through `youtube-nocookie.com` and load lazily, so they don't
  slow the page down or drop tracking cookies before someone presses play.
