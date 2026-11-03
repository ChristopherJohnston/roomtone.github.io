# Room Tone

The public pages for [Room Tone](https://roomtone.captaincourageous.co.uk), a songwriter's library of demos, mixes, stems and voice memos for Mac, iPhone, iPad and Apple Watch.

- `song.html`: where share links (`/song?library=…&song=…`) land. On an iPhone or iPad with Room Tone, a link opens the app without loading this page. Anywhere else, the page hands the link on as `roomtone://song?…`. The library and song are only ever in the link; this page sends them nowhere.
- `.well-known/apple-app-site-association`: lets the iPhone app open `/song` links (universal links).
- `CNAME`: served at roomtone.captaincourageous.co.uk.

GitHub Pages publishes the `main` branch as it is: there's no build step, and `.nojekyll` keeps `.well-known` in the published site.
