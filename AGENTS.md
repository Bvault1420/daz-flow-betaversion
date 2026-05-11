# AGENTS.md

## Cursor Cloud specific instructions

### Project overview

DayFlow 2.0 is a fully client-side Progressive Web App (PWA) serving as a live cryptocurrency dashboard. The entire app lives in a single `dayFlow2.0/index.html` file (~12k lines) with inline CSS/JS. There is no build system, no package manager, no backend, and no database.

### Running the development server

Serve the static files from the `dayFlow2.0/` directory:

```sh
npx serve -l 3000 dayFlow2.0
```

The app will be available at `http://localhost:3000/`. Service worker registration requires `localhost` or HTTPS.

### Key notes

- **No build step**: The project has no `package.json`, bundler, or transpiler. All code is inline in `index.html`.
- **No tests**: There are no automated test suites. Validation is done by loading the app in a browser and verifying live data renders.
- **No linting**: There is no linter configuration. The single HTML file contains all markup, styles, and scripts inline.
- **External API dependencies**: The app fetches live data from CoinGecko, Binance, and KuCoin public APIs. These require outbound internet access.
- **CDN dependencies**: External libraries (ethers.js, web3.js, TradingView widget, WebLLM) are loaded from CDNs at runtime — no local installation needed.
- **All state is client-side**: User data (watchlist, paper trades, wallet info) is stored in `localStorage`/`indexedDB`.
