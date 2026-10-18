# Garuda Cabs — Tirupati

A single-page taxi and cab booking website for a Tirupati-based travel operator. Covers Tirumala darshan trips, airport transfers, local sightseeing and outstation cabs, with a live fare estimator and a booking flow.

![Preview](preview.jpg)

## Features

- **Live fare estimator** — pick a route or type any distance, choose a cab type, and get an itemised quote (base fare + per-km + driver allowance + hill-route charge + 5% GST).
- **Places to Visit** — eight photo cards for real destinations around Tirupati (Tirumala, Tiruchanur, Kapila Theertham, Chandragiri Fort, Talakona, Srikalahasti, Kanipakam, Horsley Hills), each with a distance badge and a "Book this trip" button that loads the destination into the booking form.
- **Hero booking widget** — trip type, pickup, drop, date, time and cab type with an inline estimate.
- **Booking form** — validates required fields and returns a confirmation with a booking reference.
- **Fully responsive** — sticky navbar with a mobile menu, fluid grids, and a floating call/WhatsApp button.
- **No build step** — one HTML file. No frameworks, no npm, no bundler.

## Files

```
index.html    the entire site (HTML + CSS + JS in one file)
preview.jpg   full-page screenshot used in this README
```

## Running it

Just open `index.html` in a browser. That's it.

To serve it locally instead:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploying on GitHub Pages

1. Create a new repository and push this folder to it:

   ```bash
   git init
   git add .
   git commit -m "Initial commit: Garuda Cabs website"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

2. In the repository, go to **Settings → Pages**.
3. Under **Source**, choose **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, then save.
4. Your site goes live at `https://<your-username>.github.io/<repo-name>/`.

Because the entry file is named `index.html`, GitHub Pages serves it automatically with no extra configuration.

## Customising

Everything you'll want to change is in `index.html`, and most of it lives in one `<script>` block near the bottom.

| What | Where |
| --- | --- |
| Phone number, email, address | Search for `+91 98765 43210` — it appears in the navbar, contact section, footer, and the floating buttons |
| WhatsApp link | `https://wa.me/919876543210` in the floating button |
| Brand name | "Garuda Cabs" in the navbar, footer and `<title>` |
| Cab types and per-km rates | The `cabs` array — change a rate once and every quote on the page updates |
| Routes and distances | The `routes` array (drives both dropdowns) |
| Fixed "onwards" fares | The `routeGrid` array |
| Places to visit | The `destinations` array — swap `name`, `km`, `img` and `desc` |
| Minimum fare | The `MIN_FARE` constant |
| Map links | The `#mapOpen` and `#mapDir` anchors in the contact section |

### Adding a real embedded map

The contact section uses a self-contained stylised map card so it always renders, even offline. To swap in a live Google Maps embed, replace the `.map-art` div with:

```html
<iframe src="https://www.google.com/maps?q=Tirupati+Railway+Station&output=embed"
        style="width:100%;height:300px;border:0" loading="lazy" title="Location"></iframe>
```

## Note on the images

The destination and hero photographs are hotlinked from Wikimedia Commons, where they are available under Creative Commons licences (typically CC BY-SA). Two things to do before going live:

1. **Download the images and host them yourself.** Hotlinking Wikimedia is fine for a demo but isn't reliable for production, and the site won't render the photos offline.
2. **Check the licence for each file** on its Wikimedia Commons page and keep the attribution in the footer, or replace the photos with your own.

All the icons are inline SVG and the fonts load from Google Fonts, so those have no licensing concerns.

## Browser support

Tested in current Chrome, Firefox and Safari. Uses modern CSS (`:has()`, `clamp()`, CSS grid) and vanilla ES6. No IE support.

## Licence

The site code is yours to use freely. Photographs remain the property of their respective Wikimedia Commons contributors.
