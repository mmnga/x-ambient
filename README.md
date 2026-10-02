# X Ambient

Ambient light for X, Instagram, Twitch, Kick, TikTok For You and Niconico videos. Open an X post's details for automatic lighting, hover over X timeline posts or replies, browse Instagram's feed or Reels or TikTok's For You feed, or watch a video on Twitch, Kick or Niconico to illuminate the page.

English · [Español](README.es.md) · [Português Brasil](README.ptbr.md) · [日本語](README.ja.md) · [Install](INSTALL.md)

[![CI](https://github.com/mmnga/x-ambient/actions/workflows/ci.yml/badge.svg)](https://github.com/mmnga/x-ambient/actions/workflows/ci.yml)

![X Ambient preview using the included demo artwork](docs/images/preview.png)

Colors radiate from the edges of the selected media, across the margins and the backgrounds of other post cards. Photos, videos, and avatars stay sharp. The preview uses artwork included in the local demo.

## Features

- Whole-page lighting, including post card backgrounds, with an optional mode around the selected post or player.
- Automatic lighting for the opened X post on its detail page. Replies switch the light on hover; leaving a reply returns to the opened post. Media outside the viewport is excluded.
- Automatic lighting for the active Instagram feed post or Reel, without hovering. The centered post is selected, mostly visible playing videos take priority, and carousels use only their visible slide.
- Automatic lighting for the active TikTok For You video, including canvas-based playback and scroll selection. No hover is needed.
- Automatic lighting for the main video on Niconico watch pages, with native comments and player controls preserved.
- Directional, blurred light from the actual media position. Portrait videos work even inside a wider player.
- Live video colors, updated at up to 12 fps, with pause and seek support.
- Multiple photos, new timeline posts, scrolling, and X page navigation.
- Dark and light themes, plus reduced motion support.
- Adjustable intensity, blur, and spread.
- On X, intensity moves from the native theme at 0% to the original blurred media edge colors at 100%, without added saturation.
- Automatic lighting for the largest visible video on Twitch and Kick, including paused frames.
- English, Spanish, Japanese, Korean, Chinese (Simplified and Traditional), Thai, Vietnamese, Indonesian, French, German, Portuguese (Brazil and Portugal), Italian, Russian, Arabic, and Hindi, with automatic browser-language detection and a manual language selector.
- Optional X cards that fit the available window width, preserving text size and media aspect ratio. **Off by default.**

## Install in Chrome

1. Extract a localized **`x-ambient.zip`** build, or download this repository as a ZIP and extract it.
2. Open `chrome://extensions` and turn on **Developer mode**.
3. Choose **Load unpacked** and select the extracted folder containing `manifest.json`.
4. Reload a supported site. Open an X post's details or hover over a timeline post or reply, browse Instagram's feed or Reels or TikTok's For You feed, or open a video on Twitch, Kick or Niconico.

You can also clone or download this repository and load its root folder directly. Installation requires no Node.js, build step, or package installation. This project is distributed as an unpacked extension, rather than through the Chrome Web Store.

To update, replace the files in the same folder, click the extension's **Reload** button (↻), and reload the supported pages.

## Settings

Open the extension's toolbar icon. Changes apply to open supported tabs and are saved locally. **Language** follows Chrome by default, or you can choose any supported language by its native name. Unsupported browser languages fall back to English. Resetting lighting settings preserves your language choice. Chinese detection distinguishes simplified and traditional scripts, including regional browser settings for Taiwan, Hong Kong, and Macau. Portuguese distinguishes Brazil and Portugal; generic Portuguese uses the Brazilian translation. Arabic uses a right-to-left layout.

| Setting | Default |
| --- | --- |
| Ambient light | On |
| Lighting area | Whole page |
| Intensity | 65% |
| Blur | 56 px |
| Spread | 75% |
| Follow video colors | On |
| Fit X cards to window width | Off |

Window fitting uses the space available beside the navigation and sidebar. At narrower widths, the sidebar gives way to the timeline. Switching the option off restores X's layout. Saved preferences survive extension updates; **Reset to defaults** restores the values above.

![Popup in Spanish and English](docs/images/localized-popup.jpg)

## Try the demo

Clone or download this repository. With Node.js 22 or newer, run this from its root folder:

```sh
npm run demo
```

Open [localhost:4318](http://127.0.0.1:4318). The demo uses the same renderer as the extension, with original image and video assets. Try both themes, portrait video, multiple photos, and adding a new post. Press `Ctrl+C` to stop the server. Set `X_AMBIENT_DEMO_PORT` to use a different port.

## Development

No npm dependencies are needed:

```sh
npm run check
npm test
npm run package
```

Packaging uses only built-in Node.js modules and produces `output/x-ambient/` and `output/x-ambient.zip` on Windows, macOS, and Linux. Set `X_AMBIENT_OUTPUT_DIR` to choose another output directory. The archive contains the extension runtime, its license, and installation instructions. Demo assets and local test output stay out of the distribution.

See [CONTRIBUTING.md](CONTRIBUTING.md) for the code layout, manual checks, and release process. GitHub Actions checks Node.js 22 and 24; pushing a matching version tag builds a GitHub Release with the installable ZIP.

## How it works and privacy

The content script draws media from the page into small canvases, then projects their edge colors outward and blurs the result. A media mask keeps the original images and videos clear. Cross-origin canvases are displayed without reading back or exporting their pixels.

The extension uses `storage` for settings and runs only on X/Twitter, Instagram, Twitch, Kick, TikTok and Niconico pages. Translation catalogs are bundled and loaded locally. It does not capture your screen, send data to an external service, or start a second video player. Settings are stored on your device.

TikTok support covers the For You feed at `/` and `/foryou`; following feeds, profiles, search, live streams and video detail routes are outside this scope. Niconico support covers `/watch/` video pages and uses the main player rather than sidebar previews or advertising players. It follows paused and completed frames too. Neither site needs pointer input.

Instagram support covers feed posts and Reels; stories, inboxes, and profile grids are outside the current scope. The sites' page structure can change and require updates. Twitch and Kick use the largest visible HTML5 video; videos in cross-origin embedded frames are not supported. The effect pauses while the page is hidden or video is fullscreen. Player controls and chat remain interactive. Media that the browser does not allow to be drawn into a canvas, such as some protected video, is unsupported.

## License

[MIT](LICENSE), including the original demo artwork, videos, and icons. This project is not affiliated with or endorsed by X / Twitter, Instagram, Twitch, Kick, TikTok or Niconico.
