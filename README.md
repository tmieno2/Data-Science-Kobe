
# Data Science with R, Kobe University

This is the repository for the Data Science with R course website at Kobe University, where you can find lecture slides and links to the datasets used during lectures.

Please click [here](https://tmieno2.github.io/Data-Science-Kobe/) to visit the website.
## How assignments are handed out

Students download the `.qmd` from the Assignments page and write their answers
in it. Three pieces make that work, and all three matter:

1. The source lives in `assignments/<Assignment-N>/Assignment-N.qmd`.
2. `_quarto.yml` keeps `assignments/**/Assignment-*.qmd` **out** of `render:`,
   because Quarto rewrites a link pointing at a file it renders, turning the
   download link into a link to the rendered `.html`. It then lists that one
   file, by name, under `resources:`, so it is copied into `docs/` for the link
   to reach. Name each file rather than using a glob: the answer key sits in
   the same folder, and a glob would publish it.
3. `assignments/index.qmd` links to it with a `download` attribute:
   `[Assignment-1.qmd](Assignment-1/Assignment-1.qmd){download="Assignment-1.qmd"}`

Served over http the file arrives as `application/octet-stream` and the browser
saves it. Opening `docs/` straight off disk with `file://` shows the text
instead; that is a `file://` quirk, not a broken link. To check a link the way a
student will meet it, serve the folder: `python3 -m http.server` inside `docs/`.

The answer key lives beside the assignment as
`assignments/<Assignment-N>/Assignment-N-answer-key.qmd`. It stays off the site
as long as it is not named under `resources:`, which is why that list names
files one at a time, and `render:` excludes `*answer-key*` outright. The keys
are committed, so they are versioned alongside the assignment they answer.
This repository is public, so anyone who looks in it can read them; off the
website is not the same as out of reach. Render a key by hand when you want
the instructor copy.

Once an assignment ships with data files, hand out a zip built from the same
folder rather than adding a link per file, and keep the page and link shape the
same.
