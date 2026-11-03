# Rugby World Cup 2027 forecast (static site)

A single self-contained `index.html` (inline CSS and JS, no network requests, light and dark mode,
mobile friendly), ready for GitHub Pages (`.nojekyll` included). Rebuild with:

    python3 scripts/rwc2027/export_public.py
    python3 scripts/publish/rwc2027_static.py

Forecast as of 3 Nov 2026, updated 3 Nov 2026, 3:20 PM ET. Bookmaker odds are shown for comparison only and are never model inputs.

## Sources
- World Rugby match API (backs world.rugby and rugbyworldcup.com fixtures/results): https://api.wr-rims-prod.pulselive.com/rugby/v3/match?startDate=YYYY-01-01&endDate=YYYY-12-31&sort=asc&pageSize=100&page=N&sport=mru (dated n/a; accessed 2026-11-03 14:57-15:05 ET (per-request times in data/rwc2027/raw/fetch_log.csv))
- World Rugby men's rankings API: https://api.wr-rims-prod.pulselive.com/rugby/v3/rankings/mru?date=YYYY-MM-DD (dated n/a; accessed 2026-11-03 ET (281 snapshots: monthly 2003-10..2026-11 plus 2015-09-14, 2019-09-16, 2023-09-04, 2026-11-02, 2026-11-03))
- World Rugby match stats API (tries per team): https://api.wr-rims-prod.pulselive.com/rugby/v3/match/{id}/stats (dated n/a; accessed 2026-11-03 15:05-15:10 ET)
- Pools confirmed for Men's Rugby World Cup 2027 in Australia: https://www.rugbyworldcup.com/en/news/1019390/pools-confirmed-for-mens-rugby-world-cup-2027-in-australia (dated 2025-12-03 (draw in Sydney); accessed 2026-11-03 ET)
- The new Men's Rugby World Cup draw format explained: https://www.rugbyworldcup.com/2027/en/news/1019814/the-new-mens-rugby-world-cup-draw-format-explained (dated 2025-12-18 (last updated 2026-07-01); accessed 2026-11-03 ET)
- Rugby World Cup 2019 Tournament Rules: https://www.rugbyworldcup.com/en/news/35290/tournament-rules (dated n/a; accessed 2026-11-03 ET)
- 2027 Men's Rugby World Cup (third-placed team permutation table): https://en.wikipedia.org/wiki/2027_Men%27s_Rugby_World_Cup (dated n/a; accessed 2026-11-03 ET)
- Who will win the Rugby World Cup? (Paddy Power odds as of Friday September 18): https://www.mirror.co.uk/sport/rugby-union/who-win-rugby-world-cup-6467362 (dated 2015-09-18 (article 11:22 BST = 06:22 ET); accessed 2026-11-03 15:19 ET (raw/odds/mirror_paddypower_2015-09-18.html))
- The latest Rugby World Cup odds for winner, top try scorer and Wales (thepools.com prices): https://www.walesonline.co.uk/sport/rugby/rugby-news/latest-rugby-world-cup-odds-16950315 (dated 2019-09-19 21:43 ET (article 02:43 BST 20 Sep 2019); accessed 2026-11-03 15:19 ET (raw/odds/walesonline_thepools_2019-09-20.html))
- Rugby World Cup 2023 Odds: Kiwi's to open as the Betting Favourite: https://insights.betfred.com/rugby-union/rugby-world-cup-2023-odds/ (dated 2023-09-06 06:30 ET ('Prices correct as of 11:30, Wednesday 6 September, 2023'); accessed 2026-11-03 15:18 ET (read via web fetch; direct download refused with HTTP 462, so no raw copy archived))
- 2027 Rugby World Cup Outright Winner Odds (OddsJet UK, best price per team): https://oddsjet.com/en-gb/rugby-world-cup/outright-winner/odds (dated 2026-11-03 14:22 ET ('Odds updated at: 19:22 UK 03/11/2026'); accessed 2026-11-03 15:19 ET (raw/odds/oddsjet_rwc2027_outright_2026-11-03.html))
