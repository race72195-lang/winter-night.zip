# Winter Night

An animated New Year scene drawn entirely with text characters: a night sky with a moon that changes colour and phase, falling snow, a blue forest, a glowing Christmas tree with blinking lights, gifts, and fireworks you can launch with a click. It runs in the browser, with no libraries and no installation.

**Live demo:** https://race72195-lang.github.io/winter-night/

Inspired by a short video of a Python text-art “Winter Night” scene. The code here is written from scratch for the browser.

## What you can do
* **Tap or click the sky** to launch a firework (spheres, rings and hearts).
* **Fireworks** button (or Space) launches a salvo.
* **Settings:** snow amount, wind, Text or Pixels style, aurora on/off, change the moon, auto fireworks on/off.
* **Save image** (PNG) and **Record 10 s video** (WebM), so you can post the scene.
* **Hide controls** (or press H) for a clean view; double-click to bring them back.
* Countdown to New Year and greetings in Russian, Kazakh, Chinese (新年快乐, xīnnián kuàilè) and English.

## How it works
The picture is a grid of cells (about 150 × 53 on a laptop). For every cell and every frame, plain functions of its position and the time decide **colour**, **brightness** and **how dense the character should be**:

* sky: gradient + aurora from sine waves
* stars: a hash of the cell decides where they are, a sine makes them twinkle
* moon: a disc whose lit part comes from the phase formula, with crater texture from value noise
* forest and snow hills: triangle-wave silhouettes with a random height per tree
* tree: a cone with stepped tiers, shading from the left, noise texture
* decorations: baubles, light chains with a chasing blink, a five-point star with a glow
* snow and fireworks: small particle systems drawn into the same grid

Brightness and character density are separate: a dark blue forest can still be made of dense characters (`@8M$W`), while the sky uses faint dots. This was the main change that made the forest look like a forest instead of noise. At the end a small blurred copy of the picture is added on top (“bloom”) to make the lights glow. It runs at about 30 frames per second.

## Run it
Open `docs/index.html` in any modern browser (Chrome, Edge, Firefox, Safari). To get a link, turn on GitHub Pages: Settings → Pages → Deploy from a branch → `main` and folder `/docs`.

## Tested
Checked in headless Chrome on desktop and phone widths: about 30 fps, no console errors, fireworks, PNG saving and the 10-second video recording all work.

## Limitations
* No sound.
* The countdown uses the clock of your device.
* Video recording needs a browser with `MediaRecorder` (Chrome, Edge, Firefox; Safari support varies). It saves a `.webm` file.
* The scene is generated, not recorded, so it looks a bit different on every screen size.
