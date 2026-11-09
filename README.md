# gufranpathan.github.io

Source for Gufran Pathan's academic website, https://gufranpathan.github.io/.

The site is built with [Hugo](https://gohugo.io/). GitHub Actions builds and publishes it each time a change is pushed to the `master` branch (see `.github/workflows/deploy.yml`).

## Where things are

| To change | Edit |
|---|---|
| Bio ("Welcome" section) | `content/_index.md` |
| Name, title, tagline, email, interests, links | `hugo.yaml`, under `params` |
| Papers | `data/papers.yaml` |
| Links on coauthors' names | `data/coauthors.yaml` |
| Teaching | `data/teaching.yaml` |
| CV | `static/files/cv.pdf` |
| Photo | `static/images/photo.jpg` |
| Colours and layout | `assets/css/style.css` |
| Page templates | `layouts/` |

Step-by-step instructions are in [UPDATING.md](UPDATING.md).

The three coding samples from the old site are still published from `static/coding_samples/` at their old addresses, but the homepage no longer links to them.

## Preview locally

Install Hugo (extended), run `hugo server` in this folder, and open http://localhost:1313/.
