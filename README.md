# Halden

Landing hero for Halden, a fictional maritime-logistics AI company whose agent is called Hal. One HTML file, plain CSS, vanilla JS. No framework, no build step, no libraries.

## Run

Open `index.html` in a browser. It needs a network connection for two external assets:

- Inter Tight (400/500/600) from Google Fonts
- The aerial container-ship photo, served through images.higgs.ai

## What's on the page

Three scenes stacked in one scroll:

1. **Hero.** A white page with a bowl-shaped sky-cyan glow hanging from the top. It has a floating pill navbar, a two-line headline that reveals letter by letter on load, a trust line, a "Get a demo" button and a 4×2 grid of partner wordmarks.
2. **Statement.** The glow deepens and widens until the screen is solid cyan. A four-line statement pins in the middle and reveals letter by letter as you scroll. At about 40% revealed, a "Get a demo" pill pops into the navbar.
3. **Dark split.** A navy panel scrolls up. The left side has a scroll-revealed headline and a ruled info row. The right side has the ship photo, which zooms out as the panel arrives.

## How it works

- **Bowl glow.** Not an image. A 96×60 `<canvas>` is redrawn every frame and stretched to the viewport by CSS, so bilinear upscaling makes it smooth. Each pixel's colour comes from its signed distance to a curved bowl edge. The bowl's tip, width and softness are interpolated from a scroll table, with easing and a slow idle drift.
- **Letter reveal.** Text is split into per-character spans. Each character moves from invisible and blurred to a ghost colour, then an accent colour, then its final colour. Progress comes from time (hero) or scroll position (statement, dark headline).
- **Nav CTA.** The `#nav.on` class is toggled from scroll progress. It grows a dark circle at the right end, stretches it into a pill, then fades in the label.
- **Button hover.** The small cyan dot grows into a circle holding a navy chevron.

## Layout notes

- Design tokens are CSS variables in `:root` at the top of the stylesheet.
- At 820px wide or less, the nav links are hidden and the logo grid shows icons only. The statement wraps, and the split panel becomes a single column.
- The page should not scroll horizontally at 390px wide.
