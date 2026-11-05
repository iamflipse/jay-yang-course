# jay-yang-course

An interactive course site built with [mdbook](https://rust-lang.github.io/mdBook/) from Jay Yang's "Full Courses" trilogy (his "trilogy" referenced in the Oct 30 2026 X post).

**Public copy:** <https://iamflipse.github.io/jay-yang-course/> (read-only; static build of `src/` served from the `gh-pages` branch)

Companion to the [jay-yang-wiki](https://github.com/iamflipse/jay-yang-wiki) repo, which holds the raw sources (transcripts) and distilled concept notes. This repo holds the course presentation layer.

## Contents

- **Part 1 — Copy Thinking**: marketing foundations, the six P's of copy thinking, empathy maps & sales-call mining
- **Part 2 — Personal Brand**: PTL (power/trust/likeness), current vs future demand, content multiplication (Hall of Fame + 3 R's)
- **Part 3 — Paid Ads**: the 5-step ad writing process (story bible, why-they-buy sheet, awareness levels, market sophistication, unique mechanism, big idea), media buying principles
- **Practice**: workbook exercises

## Layout

- `src/` — markdown chapters + `SUMMARY.md`
- `book/` — mdbook-generated static site (committed so GitHub Pages can serve it)
- `tools/mdbook` — mdbook v0.4.21 binary (aarch64 Linux, built from source)

## Deploying updates to the live site

The live site is served from the `gh-pages` branch (repo is public so GitHub Pages works on the free plan). To republish after editing `src/`:

```sh
./tools/mdbook build -d book                      # rebuild book/
git add -A && git commit -m "update" && git push origin main
git checkout --orphan gh-pages                     # rebuild the gh-pages branch
rm -rf ./* && mv book/* . && git add -A
git commit -m "publish" && git push -f origin gh-pages
git checkout main
```

## Rebuild

```sh
cd /path/to/jay-yang-course
./tools/mdbook build -d book
```

## Serve locally

```sh
./tools/mdbook serve
```
