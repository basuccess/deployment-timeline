# Deployment Timeline: Fiber vs. ngFWA

An interactive, single-file web widget that visualizes how long it takes to start
earning revenue with fiber versus next-generation fixed wireless access (ngFWA).
Move the permitting-delay slider or toggle complex terrain, and the timeline and
summary stats update instantly to show the revenue that fiber's build-out timeline
leaves on the table.

## Live demo

Once published to GitHub Pages: `https://<your-username>.github.io/deployment-timeline/`

## What it shows

The chart plots two deployment tracks against a shared "months from network launch"
axis:

- **ngFWA** — a fast track (Survey → Install → Activate) that reaches its green *Start Revenue* line at month 6.
- **Fiber** — a slower track (Design → Permitting → Construction) whose *Start
  Revenue* point moves later as permitting drags on.

The gray dashed **Lost Revenue Zone** between the two revenue-start points is the
window in which ngFWA is already earning while fiber is still being built.

Three summary figures update live:

- **Fiber Revenue Start** — the month fiber begins earning
- **ngFWA Revenue Start** — fixed at month 6
- **Lost Revenue Period** — the gap between the two

## Controls

- **Permitting Delay (Months)** — slider, 6 to 24 months
- **Complex Terrain / Env. Review** — toggle that adds 6 months of permitting

## The model

The timeline is driven by a few simple, adjustable assumptions:

| Track | Phases | Revenue starts |
| --- | --- | --- |
| ngFWA | Survey + Install + Activate (~5 months) | Fixed at month 6 |
| Fiber | Design (2 mo) + Permitting (slider) + Construction (6 mo) | 8 + permitting delay |

Complex terrain / environmental review adds 6 months to the permitting phase.
Lost revenue period = Fiber Revenue Start − 6.

All of these numbers live as named constants at the top of the `<script>` block in `index.html` (`NGFWA_START`, `SURVEY`, `CONSTRUCTION`, `TERRAIN_ADD`) and can be
changed in seconds.

## Usage

No build step, no dependencies, no tracking. It is one self-contained HTML file with
inline CSS and JavaScript.

- **View locally:** double-click `index.html` to open it in any browser.
- **Share:** host the file anywhere that serves static pages (GitHub Pages, Netlify,
  your own site) and share the link.

## Deploy to GitHub Pages

1. Create a **public** repository and upload this file as `index.html`.
2. Go to **Settings → Pages**.
3. Set **Source** to *Deploy from a branch*, branch `main`, folder `/ (root)`, and
  save.
4. After a minute, your public URL appears at the top of the Pages settings screen.

## Customization

- **Timeline numbers:** edit the constants at the top of the script.
- **Phase labels:** the ngFWA green blocks (`Survey`, `Install`, `Activate`) and the
  fiber bars (`Design`, `Permitting`, `Construction`) are plain strings in the draw
  function.
- **Colors:** defined as CSS variables in the `<style>` block (`--green`, `--blue`, `--blue-strong`, `--gray-zone`).
- **Axis:** `MAX_MONTHS` sets the plotting scale; `AXIS_MAX` sets where the visible
  grid and month labels stop.

## License

Internal / promotional use.
