# Room Tone

The public pages for [Room Tone](https://roomtone.cloud), a songwriter's library of demos, mixes, stems and voice memos for Mac, iPhone, iPad and Apple Watch.

- `privacy.html` and `support.html`: the privacy policy and support page App Store Connect links to, at `/privacy` and `/support`. The privacy page has to match the app's App Privacy answers there; change both together.
- `song.html`: where share links (`/song?library=…&song=…`) land. On an iPhone or iPad with Room Tone, a link opens the app without loading this page. Anywhere else, the page hands the link on as `roomtone://song?…`. The library and song are only ever in the link; this page sends them nowhere.
- `.well-known/apple-app-site-association`: lets the iPhone app open `/song` links (universal links).
- `CNAME`: served at roomtone.cloud.

GitHub Pages publishes the `main` branch as it is: there's no build step, and `.nojekyll` keeps `.well-known` in the published site.

## Screenshots

`images/` holds the home page's screenshots, from the example library only (never a real one), as WebP, light and dark.

- **The Mac:** drawn by the app's own test, at 2× (2880 × 1800), then `cwebp -q 85`:

  ```sh
  cargo run --release -p roomtone-library --example example_library
  ROOMTONE_SCREENSHOTS=~/Desktop/shots cargo test -p roomtone-ui website_screenshots -- --ignored
  ```

- **The iPhone:** from the simulator (iPhone 16 Pro), launched with the app's launch settings on a copy of `apps/ios/Example/Example Songs` (`ROOMTONE_FOLDER`, `ROOMTONE_SONG`, `ROOMTONE_PLAY`, `ROOMTONE_MUTE`), the status bar set with `xcrun simctl status_bar … override --time 9:41`, and the appearance with `xcrun simctl ui … appearance light|dark`. Taken with `xcrun simctl io … screenshot`, halved, then `cwebp -q 85`.

`style.css` is linked as `style.css?4`: browsers keep it for ten minutes, so when it changes, raise the number in every page, or a page can arrive with the old stylesheet.
