# Seeing the Shape of Space

*Determine the spatial geometry of your universe.*

A browser game for an introductory cosmology course. Students fly a spaceship through a three-dimensional universe whose shape is hidden from them. Using only measurements they can make from the inside, they work out whether space is flat or curved, and finite or infinite.

Created by Dr. Alex Sobotka.

## Play

Open `index.html` in any modern browser (Chrome, Edge, Firefox or Safari) on a laptop or desktop. Nothing to install or build: the whole game is this one file.

To put it online with GitHub Pages:

1. Upload `index.html` and `README.md` to a GitHub repository.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, then **Save**.
4. After a minute or two the game is live at `https://<your-username>.github.io/<repository-name>/`.

## The four universes

| Curvature | Shape | Extent | What students can observe |
|---|---|---|---|
| Flat | Plane | Infinite | Triangles add to 180°. Parallel torpedoes stay the same distance apart. Flying straight never brings you home. |
| Flat | Torus | Finite | Triangles add to 180° and parallel torpedoes stay apart, but flying straight brings you home, and small tori show repeated copies of Earth. |
| Positive | Sphere | Finite | Triangles add to more than 180°. Parallel torpedoes come together and cross. Flying straight brings you home. |
| Negative | Saddle | Infinite | Triangles add to less than 180°. Parallel torpedoes spread apart. Flying straight never brings you home. |

The torus, sphere and saddle come in a range of sizes. A very large curved universe looks almost flat unless students make big measurements, just as in the real universe.

## How a game works

1. Press **Start**. You get a **mystery universe** with its shape hidden, at a random size. By default the shapes come in a random order, and each student sees all four shapes before any shape repeats (see *Order of mystery shapes* below). Earth, your home, is just ahead of the ship.
2. Explore and measure (see below).
3. Choose a shape from **Your guess** and press **Check guess**. The answer is revealed, and the minimap appears showing the 2D analogy of your universe (a plane, torus, sphere or saddle) with your path, triangle and torpedo trails on it. Drag the minimap to turn it.
4. Press **New mystery** for another universe, or click the title to return to the start screen.

### Flying

| Key | Action |
|---|---|
| ← → | Turn left and right |
| ↑ ↓ (or W S) | Nose up and down |
| Space (hold) | Fly |
| Shift (hold) | Warp speed, about five times faster |
| L | Straight-line lock: steering is disabled so you fly perfectly straight |
| H | Back home (also clears measurements) |

On-screen buttons do the same things for touchscreens.

### Measuring

| Key | Tool | What it shows |
|---|---|---|
| B | **Drop beacon** | Drop three beacons. Laser beams, the straightest possible lines, join them into a triangle, and its three angles and their sum are shown. |
| P | **Fire torpedoes** | Two torpedoes fly off side by side, pointing exactly the same way. A graph shows how the separation between them changes as they travel. |
| T | **Show path** | Your path over the last minute is traced in the view. |
| C | **Clear** | Removes beacons and torpedoes. |

**Landmarks:** Earth and three one-of-a-kind objects (a gold-and-magenta nebula, a large teal spiral galaxy and an edge-on galaxy) appear only once in each universe. If you see one of them twice, light has gone all the way around the universe.

## For instructors

Click the **⚙ gear** button in the top bar and enter the passcode. From there you can:

- switch to **explore mode**, which shows the shape buttons, the size slider and the minimap so you can demonstrate any universe;
- start a **new mystery universe**;
- see the **answer** to the current mystery.

- choose the **order of mystery shapes** (below).

Tick **Remember on this device** to skip the passcode next time, and use **Lock settings** to lock it again.

### Order of mystery shapes

| Setting | What students get |
|---|---|
| `cycle` (default) | All four shapes once, in a random order, before any shape repeats. Then a new random round begins, never starting with the shape just seen. |
| `norepeat` | A random shape each time, but never the same shape twice in a row. |
| `random` | A completely random shape each time. |

Each browser keeps its own place in the order, and it survives reloading the page.

A setting chosen in the ⚙ menu applies only to that computer. To set the order for a whole class, give students a link ending in the setting, for example `https://<your-username>.github.io/<repository-name>/#norepeat`. The ⚙ menu shows the link for the current setting with a **Copy link** button. To change the default for everyone, edit this line in `index.html`:

```js
const ORDER_DEFAULT='cycle';
```

### Passcode

**The default passcode is `shape`.** To change it, open `index.html` in a text editor, find this line and replace the text between the quotes:

```js
const TEACHER_PASSCODE='shape';
```

The passcode only keeps students from stumbling into the answer. Anyone who opens the page source, which is public on GitHub, can read it.

## Sound

The game has its own soundtrack ("Hyperdrive", about 2 minutes 43 seconds: intro, verses, choruses, a bridge and an outro that loops back to the start) and sound effects for the engine, warp, beacons, torpedoes and getting home. All of it is generated live in the browser with the Web Audio API, so there are no audio files. Music starts when a player presses **Start**. Volume sliders and a mute switch are under **Menu**, and the browser remembers the settings.

## Technical notes

- Single self-contained HTML file: HTML, CSS and JavaScript, with no libraries and no build step.
- The only outside resources are three Google Fonts (Big Shoulders Display, IBM Plex Sans and IBM Plex Mono). Without internet access the game still works, with system fonts.
- The 3D view shows each galaxy where light would actually reach you from in that geometry: along great circles on the sphere, along hyperbolic straight lines on the saddle, and wrapping around on the torus. That is why repeated images appear in small finite universes.
- Settings (sound, instructor unlock, last mystery shape) are saved in the browser's local storage. Nothing is sent anywhere.
- The ship and torpedoes are drawn far larger than true scale.
- Designed for laptop and desktop screens. It fits a typical laptop browser window without scrolling.
