# How to Update Your Website

Everything on the site can be edited directly on GitHub in your browser — no software to install. Open <https://github.com/joaquimmeira/jmeira.github.io>, navigate to the file you want, click the pencil icon to edit, and click **Commit changes**. The site rebuilds and goes live automatically within about 2 minutes.

The site has four pages: the homepage (`content/_index.md`), Research (`content/research.md`), Teaching (`content/teaching.md`), and a Portuguese homepage (`content/_index.pt.md`, shown at `/pt/`). The papers and teaching lists live in the `data/` folder and are rendered onto their pages automatically.

## Add or update a paper

Edit `data/papers.yaml`. Each paper looks like this:

```yaml
- title: "Your Paper Title"
  coauthors:                      # delete this block if solo-authored
    - name: "Coauthor Name"
      url: "https://their-website.com/"
  status: "working paper"         # see options below
  venue: "Journal Name"           # only for published/accepted/R&R papers
  abstract: >-
    One paragraph abstract here.
```

Status options: `published`, `accepted`, `revise and resubmit`, `under review`, `working paper`, `work in progress`.

To link a PDF: upload it to `static/files/` (in the repo, open that folder → **Add file** → **Upload files**), then the file will be available at `www.jmeira.com/files/your-file.pdf`.

## Mark a paper as published

In `data/papers.yaml`, change its `status` to `"published"` and set `venue` to the journal name.

## Update your bio or tagline

- English: edit `content/_index.md`
- Portuguese: edit `content/_index.pt.md`

The text below the `---` lines is the bio. The lines between the `---` markers control the tagline and the contact blurb. The teaching page's intro and advising note are in the front matter of `content/teaching.md`.

## Add a teaching entry

Edit `data/teaching.yaml` and add an entry at the top (the list shows in file order):

```yaml
- course: "Course Name"
  code: "GOV 123"                 # optional
  role: "Teaching Fellow"         # or "Lead Instructor" / "Teaching Assistant"
  institution: "Harvard University"
  term: "Fall 2026"
  instructor: "Prof. Name"        # optional
```

## Update your CV

The CV's LaTeX source lives next to this repo in `Website\cv\cv.tex`. Edit it, then run (in PowerShell, from the `cv` folder):

```powershell
.\publish-cv.ps1            # compile and copy the PDF into the repo (nothing goes live)
.\publish-cv.ps1 -Publish   # also commit and push — live on the site in ~2 minutes
```

Alternatively, replace `static/files/CV_Meira.pdf` with any new PDF, **keeping the same filename** (in the repo, open `static/files/`, then **Add file** → **Upload files** and upload a file named exactly `CV_Meira.pdf` — it will replace the old one).

## Change your photo

Replace `static/images/photo.jpg` the same way (upload a new JPEG named exactly `photo.jpg`). A roughly square crop looks best — it displays as a circle.

## Remove the footer credit or metadata

In `hugo.yaml`, under `params: mysite:`, set `credit: false` to remove the footer credit line and/or `discovery: false` to remove the invisible generator metadata.

## If something breaks

Every change is saved in git history, so nothing is ever lost. In the repo, click **History** on any file to view or restore an earlier version. Deploys run under the **Actions** tab — if the site didn't update, check there for a red ✗ and open the log.
