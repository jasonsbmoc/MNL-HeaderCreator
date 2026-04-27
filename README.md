# MNL Header Creator

Internal tool for generating Medium Newsletter header images.

## What it does

Composites three layers into a 2000×500px banner and exports as PNG:

1. **Background** — grayscale photo, pan/crop-able
2. **Title overlay** — transparent PNG from a pre-exported set
3. **Grain texture** — single PNG, overlay blend mode

## Usage

Open the deployed page. Controls left to right:

| Button | Action |
|--------|--------|
| ↺ | Randomize everything (new background + new title) |
| Random title | Pick a new title overlay, keep current background |
| Upload image | Use your own background photo |
| Random image | Pick a random photo from the bank |
| Mark as used | Permanently retire the current bank image |
| Download | Export the full 2000×500px PNG |

When **Upload image** is active, a zoom slider appears below the controls for adjusting crop.

Drag directly on the preview canvas to pan the background image.

## Assets

| Path | Description |
|------|-------------|
| `/images/bank/` | Background photo pool (`mnl-bg-01.jpg` … `mnl-bg-50.jpg`) |
| `/images/text/` | Title overlay PNGs, 2000×500px with transparent background |
| `/images/grain.png` | Grain texture, 2000×500px |
| `/used.json` | List of retired bank images |

## Managing the image bank

**Retire an image:** use the "Mark as used" button in the tool. This appends the filename to `used.json` via the GitHub API and removes it from the current session's pool.

**Restore an image:** remove its filename from the `"used"` array in `used.json` and push.

**Add images:** drop new files into `/images/bank/` following the `mnl-bg-XX.jpg` naming convention and push.

## Deployment

Hosted via GitHub Pages from the `main` branch root.
