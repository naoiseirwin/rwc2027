# Rugby World Cup 2027 forecast

**Live site:** https://naoiseirwin.github.io/rwc2027/

A probabilistic forecast of the 2027 Men's Rugby World Cup in Australia: each team's chance of winning the tournament, reaching each knockout stage, and winning each of the 36 pool matches. Forecast as of 3 Nov 2026, using results through 31 Oct 2026.

This is a personal project for fun and interest. It is not betting advice.

## Headline odds (as of 3 Nov 2026)

| Team | Model | Bookmaker implied* |
|---|---|---|
| South Africa | 32.7% | 25.4% |
| New Zealand | 29.9% | 16.9% |
| Ireland | 13.1% | 9.5% |
| France | 7.9% | 17.6% |
| Australia | 7.0% | 8.5% |
| England | 5.4% | 10.9% |
| Scotland | 2.6% | 2.9% |
| Argentina | 1.4% | 4.5% |

*OddsJet UK best price per team, quoted 3 Nov 2026 2:22 PM ET. Shown for comparison only; odds are never an input to the model.

## How the model works

- **Team strength.** Each team's strength is a 50/50 blend of two things: our own rating, built from every men's Test result since 2003, and the official World Rugby rankings.
- **Matches.** A strength gap turns into a probability of winning and an expected winning margin for each match.
- **Tournament.** The whole tournament is simulated 100,000 times (random seed 0). That covers pool matches with bonus points, pool tiebreaks, the best-third-place rule in the new 24-team format, and the knockout bracket. Each team's odds are the share of simulations it wins.
- **No peeking.** Model settings were fixed ("frozen") using pre-2015 data only before any test was scored. Each backtest uses only data available before that tournament's opening match.

## How well it has done (backtests)

The same model, with the same frozen settings, was run on the last three World Cups as if forecasting them beforehand: 141 matches in all. Lower scores are better.

**Match predictions (log loss)**

| | 2015 | 2019 | 2023 |
|---|---|---|---|
| This model | **.344** | **.331** | **.338** |
| Our ratings alone | .351 | .342 | .340 |
| World Rugby rankings alone | .347 | .341 | .364 |
| World Rugby's simple prediction formula | .360 | .406 | .391 |

The blend was the best at predicting matches in all three tournaments.

**Where it lost**

- World Rugby's simple formula was better at predicting how far each team would go in 2015 and 2019.
- In every year, at least one benchmark gave the eventual champion more probability than we did. In 2015 we gave New Zealand 56%, the formula gave them 67% and the bookmaker 39%. In 2019 we gave South Africa 14% and the bookmaker 17%. In 2023 we gave South Africa 21% and the formula 23%.
- The model is slightly cautious on 60–90% favourites and slightly overconfident at 90%+.

**A rejected upgrade.** A second version added home advantage, travel and rest effects, more weight on recent form, and fatter-tailed margins. It was frozen on pre-2015 data and then tested the same way. It scored worse (log loss .351 vs .338), so it was not adopted.

## Caveats and items to confirm

- The 2027 points and bonus rules are assumed to match 2019's.
- The pool tiebreak order and the best-third-place table still need checking against World Rugby's official publications.
- Drawn knockout matches are treated as 50/50.
- Travel, rest and squad changes are not modelled.
- Three tournaments is a small test sample.

## About this repo

`index.html` is the whole site: one self-contained file with no network requests, light and dark mode, and mobile friendly. It is generated from a private forecasting framework, which is not included here.

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
