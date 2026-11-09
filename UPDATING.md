# How to update the website

You can make every change below on GitHub, in your web browser. Open the file in the repository, click the pencil icon to edit it, and then click "Commit changes". GitHub rebuilds the site after each commit to the `master` branch, and the change appears at https://gufranpathan.github.io/ about two minutes later. The "Actions" tab of the repository shows each rebuild and whether it succeeded.

The `.yaml` files in the `data` folder hold the lists on the homepage. They depend on indentation. To add an entry, copy an existing entry, paste it, and edit the text between the quotes. Keep the same number of spaces at the start of each line.

## Add a new paper

1. Upload the PDF, if you have one. Open the folder `static/files`, choose "Add file" and then "Upload files". Give the file a short name with no spaces, such as `polarization-names.pdf`.
2. Open `data/papers.yaml`. Copy an existing entry and paste it where you want the paper to appear. Papers appear on the site in the order of this file.
3. Edit the fields and commit the change.

An entry looks like this:

```yaml
- title: "Paper Title"
  authors: ["First Coauthor", "Gufran Pathan", "Second Coauthor"]
  year: 2027
  status: "working paper"
  venue: ""
  pdf: "files/paper-title.pdf"
  link: ""
  abstract: ""
  job_market_paper: false
```

- `authors` lists every author in order, including you. The site leaves out your name and shows the others as "with A, B and C". To link a coauthor's name to a web page, see "Link a coauthor's name" below.
- `status` must be one of `published`, `accepted`, `revise and resubmit`, `under review`, `working paper` or `work in progress`. It appears as a small label next to the title.
- `pdf` is the path of the uploaded file, starting with `files/`. When `pdf` is set, the title links to the PDF.
- `link` is a web address for the paper, such as an SSRN or journal page. The title links to it when there is no PDF.
- `abstract` is optional. When it is set, visitors can open the abstract under the title.

## Link a coauthor's name

Open `data/coauthors.yaml`, copy an entry, and edit it:

```yaml
- name: "Coauthor Name"
  url: "https://example.edu/coauthor/"
```

Spell the name exactly as it appears in `data/papers.yaml`. The name then links to that address in every paper it appears on. A coauthor without an entry appears without a link.

## Mark a paper as published

Change its `status` to `"published"`, put the journal name in `venue` and the year in `year`, and put the DOI or journal address in `link`. The paper then moves from "Working Papers" to "Publications".

## Add your job market paper

Set `job_market_paper: true` on that paper, and give it an `abstract` and a `pdf`. The site shows it first in the Research section, in a shaded box with the full abstract and a link to the PDF.

## Update your bio

Edit `content/_index.md`. The text below the second `---` line is the "Welcome" section. Leave a blank line between paragraphs. To add a link, write `[link text](https://example.com)`.

Your name, title, tagline, email address and research interests are in `hugo.yaml`, under `params`.

## Add a teaching entry

Open `data/teaching.yaml`, copy an entry, and edit it. Entries appear in the order of the file, so put the newest first. The `role` field (for example "Graduate Student Instructor") and the `instructor` field are optional. Leave them as `""` to hide them.

## Update your CV

Upload the new PDF to `static/files` with the name `cv.pdf`, so that it replaces the old file. Every CV link on the site points to this file, so the name must stay the same.

## Change your photo

Upload the new photo to `static/images` with the name `photo.jpg`. The site shows it as a 4:5 portrait, so crop it to that shape first, for example to 400 × 500 pixels. Keep the file under about 200 KB so that the page loads quickly.

## Add a news item

Create the file `data/news.yaml` if it does not exist yet (choose "Add file" and then "Create new file"). Add items with the newest first:

```yaml
- date: "Mar 2027"
  text: "Presented a paper at the Midwest Political Science Association conference."
```

A "News" section appears on the homepage as soon as the file has an entry. It shows the eight most recent items.

## Add an award or fellowship

Create the file `data/awards.yaml` and add entries:

```yaml
- name: "Name of the award or fellowship"
  year: "2027"
```

An "Awards and Fellowships" section then appears on the homepage.

## Add a blog post

1. If this is the first post, create the file `content/blog/_index.md` with these lines:

   ```yaml
   ---
   title: "Blog"
   ---
   ```

2. Create the file `content/blog/your-post-name/index.md`, with a short name of your choice in place of `your-post-name`:

   ```yaml
   ---
   title: "Post Title"
   date: 2026-11-09
   description: "One-sentence summary."
   ---

   The text of the post, in Markdown.
   ```

   Set `date` to the day you publish the post. A post dated in the future does not appear on the site until that day.

3. To add a "Blog" link to the top bar, add this entry under `menus` and then `main` in `hugo.yaml`:

   ```yaml
       - name: "Blog"
         url: "/blog/"
         weight: 35
   ```

The homepage lists the five most recent posts once the first post exists.

## Add a link under your photo

In `hugo.yaml`, under `params`, replace the line `social: []` with lines like these:

```yaml
  social:
    - name: "Google Scholar"
      url: "https://scholar.google.com/citations?user=YOUR_ID"
      icon: "link"
```

Keep the spaces at the start of each line. Each link is one entry of three lines, starting with `- name:`. The `icon` can be `github` or `link`. The links appear under your photo and in the Contact section.

## Add software or other projects

Create the file `data/projects.yaml` and add entries:

```yaml
- name: "Project name"
  description: "One sentence on what it does."
  url: "https://github.com/gufranpathan/project-name"
  language: "R"
```

A "Projects" section then appears on the homepage, below Research. To give it another heading, such as "Software", add the line `projectsHeading: "Software"` under `params` in `hugo.yaml`.

## Old coding samples

The three coding samples from the old site are still in `static/coding_samples`. They still work at their old addresses, such as https://gufranpathan.github.io/coding_samples/rdd_elite_colleges.html, but the homepage does not link to them. To take them off the web, delete that folder.

## Change the look of the site

The colours are set at the top of `assets/css/style.css`, in the block that starts with `:root`. Each line sets one colour. For example, `--color-accent` is the colour of links.

The current design is modeled on two sites you chose, tarahein.com and bouchat.github.io. They are recorded in `hugo.yaml` under `params.mysite.design`. To get a different design, ask your AI assistant to run the design quest at https://gking.harvard.edu/mysite/files/QUEST_DESIGN.md and show you three previews.

Two settings in `hugo.yaml` under `params.mysite` are switched off. `credit: true` would add the line "Created using GaryKing.org/mysite" to the footer. `discovery: true` would add an invisible generator tag and a schema.org description of you for search engines.

## Preview changes on your computer (optional)

You do not need this to edit on GitHub. To see a change before publishing it, install Hugo (extended), open a terminal in this folder, run `hugo server`, and open http://localhost:1313/. The page reloads each time you save a file.

If you change the Hugo version on your computer, also change `HUGO_VERSION` in `.github/workflows/deploy.yml`, so that GitHub builds the site with the same version.
