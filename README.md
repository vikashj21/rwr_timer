# RWR Showcase Timer

Full-screen run timer for the Real World Robotics Task 1 demo day (Sim2Real cube rotation on the ORCA v2 hand).

- Setup screen: team name, Subtask 1 / 2 / 3 or Presentation, Run 1 / 2 / 3, timer 1 min, 5 min or Custom (minutes + seconds). Picking a subtask sets the timer to 1 min, picking Presentation sets it to 5 min (both can be changed by hand).
- Optional countdown before start: tick "Countdown before start" and set the seconds (1–60, default 5). The run screen then counts down with a beep each second before the timer starts; Restart and Run again repeat it. The setting is remembered on the device.
- Run screen: team name in the top 25% (black on white), subtask and run below it, then a large countdown that turns amber at 30 s, red at 10 s, and beeps at zero.

It is a static page: `index.html` plus the logos and icons in `assets/`, with no build step and no dependencies (fonts load from Google Fonts and fall back to system fonts when offline).

## Open it

- **From the repo:** open `index.html` in any browser.
- **From a link:** enable GitHub Pages (Settings → Pages → Deploy from branch → `main` / root). The timer is then at `https://<user>.github.io/<repo>/`.
- **iPad, true full screen:** open the link in Safari, then Share → Add to Home Screen, and launch it from the home screen icon.
- **iPad without internet:** run `python3 -m http.server 8000` in this folder on a laptop and open `http://<laptop-ip>:8000` on the iPad (same Wi-Fi).

## Controls on the run screen

| Button | Key | Action |
|---|---|---|
| Pause / Resume | P | Pause or resume the countdown |
| Restart | R | Restart the current run from full time |
| Next run | N | Back to setup with the run number +1, to pick the next timer |
| Edit setup | E | Back to setup |
| Sound on/off | | Toggle the time's-up beep |
| Fullscreen | F | Toggle browser fullscreen |

While the clock is running, Restart, Next run and Edit setup need a second tap so a stray touch can't end a demo. The iPad silent switch mutes the beep.

## Customising

Everything is in `index.html` (images in `assets/`):

- Colors and fonts: the `:root` tokens at the top of the `<style>` block.
- Subtask names: `SUBTASKS` at the top of the `<script>` block (and the labels in the setup form).
- Default timer per subtask: `DEFAULT_MIN` next to `SUBTASKS`.
- Timer options: the `name="dur"` radio buttons (value is minutes, `c` = custom). The default custom time is the `value` of `cMin` / `cSec`.
- Warning thresholds: `WARN_MS` and `STOP_MS` in the script.
- Logos: the SRL | ETH lockup (`assets/srl-logo.png`, `assets/eth-logo.png`) sits at the top of the setup header and in the middle of the run screen's subtask/run band (hidden below 700 px wide). `assets/hand-cube.png` (the RWR logo) is next to the setup title and is the source of `favicon.png` and the iPad home-screen `apple-touch-icon.png`.
