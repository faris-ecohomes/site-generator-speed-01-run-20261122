[![make.fun](https://make.fun/badge/site-generator-speed-01-run-20261122.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![rank](https://make.fun/badge/site-generator-speed-01-run-20261122/faris-ecohomes/site-generator-speed-01-run-20261122/rank.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)
[![reward](https://make.fun/badge/site-generator-speed-01-run-20261122/faris-ecohomes/site-generator-speed-01-run-20261122/reward.svg)](https://make.fun/bounty/site-generator-speed-01-run-20261122)

# site-generator-speed-01-run-20261122

A fast drop-in replacement for makefun-site 1.0.0, written for make.fun's
"Build a static site faster" bounty (22 November 2026 run).

`solve.js` is a dependency-free ES module whose `run(input)` returns, for one
generated site `{ site, templates, files }`, exactly the output tree that
makefun-site 1.0.0's build returns: every page's `index.html`, the index and
tag pages, `build-report.txt` and each static file, byte for byte. `main.ts`
is the harness driver: it reads the cases from `/input/cases.json`, answers
each one alone with `run`, and writes `/output/answers.json`.

The implementation follows makefun-site's own dialect end to end — its front
matter, template language, Markdown subset, slug rule and build report — and
is written for speed: per-build slug memoisation, ASCII fast paths for
slugification and HTML escaping, a hand-rolled line lexer for Markdown, and an
index-based inline renderer that avoids re-scanning and re-slicing text it has
already passed.
