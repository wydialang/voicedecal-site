# Voice DeCal course website

The course website is a [Jekyll](https://jekyllrb.com/) site built with the
[Just the Docs](https://just-the-docs.com/) theme.

---

## Publishing / hosting status
TODO


---

## Editing common things
Any list-based content that needs to be updated over time, like the staff info and the course schedule, are rendered from `.yml` files in `_data`. The rest of the content and the webpages themselves are edited in Markdown.

| To change… | Edit… |
|:-----------|:------|
| Site title, footer, theme color, Syllabus/Discord links, settings | [`_config.yml`](_config.yml) |
| Home page | [`index.md`](index.md) |
| The course-schedule table (weeks, topics, activities, links) | [`_data/schedule.yml`](_data/schedule.yml) |
| Which schedule week is "current" | `current_week` in [`_config.yml`](_config.yml) |
| Google Calendar embed | [`calendar.md`](calendar.md) |
| Grading, attendance, integrity, accommodations (currently unused) | [`policies.md`](policies.md) |
| Facilitator profile cards | [`_data/staff.yml`](_data/staff.yml) |
| Faculty sponsor, contributors, contact table | [`staff.md`](staff.md) |
| What the DeCal is, how to enroll | [`about.md`](about.md) |
| Colors of a theme | `_sass/color_schemes/light1.scss`, `dark1.scss`, … (see below) |
| Logo / hero art | files in [`assets/images/`](assets/images/) — see its `README.md` |
| Which semester the site is for | `semester` / `semester_short` in [`_config.yml`](_config.yml); full rollover in [`ROLLOVER.md`](ROLLOVER.md) |

### Course links

The course links are set near the top of
[`_config.yml`](_config.yml). They feed the top-right menu bar and every other page that references the links. For example, links to the syllabus/Discord can be referenced as `{{ site.syllabus_url }}` /
`{{ site.discord_url }}` in the Markdown; `%syllabus%` / `%discord%` in
announcement entries.


### Course schedule (Home page)

The schedule is one YAML block per week in [`_data/schedule.yml`](_data/schedule.yml). Each week takes:

```yaml
- week: 7
  date: "10/26"
  topic: Voice Modulation II       # the bold heading
  points:                          # bullets under the heading (optional)
    - Distortion
    - False chords
  assignment:                      # one line each (optional)
    - Storytelling exercise
  resources:                       # one line each (optional)
    - Real-time spectrogram | https://spec.sumianvoice.com/   # "label | url" makes a link
    - TBD                                                     # plain text is left as-is
```

Wrap a value in quotes if it contains a colon or starts with punctuation.
Set `current_week` in [`_config.yml`](_config.yml) to move the "Skip to current
week" button and the row highlight.

### Facilitators (Staff page)

Same idea; one block per person in [`_data/staff.yml`](_data/staff.yml):

```yaml
facilitators:
  - name: lydia wang
    photo: tetomuni.png            # a file in assets/images/ (cropped to a square)
    bio: >
      short paragraph, *Markdown* and [links](url) allowed
    contact: you@berkeley.edu      # a bare email links itself; else Markdown
```

The profile cards are rendered with the photo beside the text, alternating left/right down the
list, and stacking on phones. The rest of the Staff page (faculty sponsor,
contributors, contact table) can be edited directly in [`staff.md`](staff.md).

### The Google Calendar (schedule page)

Replace the calendar link in [`calendar.md`](calendar.md) according to the instructions below:

1. Create a Google Calendar named `Voice DeCal <SEMESTER>`
2. Go to that calendar's settings. 
3. Under `Access permissions for events`, make sure the calendar is made available to the public with `See event details`.
4. Under `Integrate calendar`, copy the public URL to the calendar. Replace the link in `calendar.md` with the copied URL and add `&mode=WEEK` to the end of the URL.


### Announcements

The home-page announcements block is **off** by default. To use it: set
`announcements_enabled: true` in [`_config.yml`](_config.yml) and add entries to
[`_data/announcements.yml`](_data/announcements.yml) (each has a `date` and a
`body`; Markdown and links are allowed in `body`). Set it back to `false` to
hide the whole section.

### Color themes

There are currrently three theme **sets**, each with a light and a dark version, as files in `_sass/color_schemes/`:

| Set | Light | Dark | Look |
|:----|:------|:-----|:-----|
| 1 | `light1.scss` | `dark1.scss` | Teal |
| 2 | `light2.scss` | `dark2.scss` | Blue & pink |
| 3 | `light3.scss` | `dark3.scss` | Miku (teal + pink) |

On the site, visitors can **flip light/dark** with the top-bar button and **cycle
between sets** by clicking the logo above the sidebar. Their choice is saved in their browser;
until they choose, the light/dark half follows their computer's setting.

- **To recolor a theme:** edit the variables at the top of that `.scss` file.
  Besides the theme's own colors, each scheme can set these knobs (defined in
  [`_sass/custom/custom.scss`](_sass/custom/custom.scss)).
  Keep light-mode text colors at 4.5:1 contrast on their background
  (check at <https://webaim.org/resources/contrastchecker/>).
- **To change which theme new visitors see first:** set `color_scheme:` in
  `_config.yml` to one of the six names (use a `light` one).
- **To add a 4th set:** copy `light3.scss`/`dark3.scss` to `light4.scss`/
  `dark4.scss`, copy `assets/css/just-the-docs-light3.scss` likewise (change
  the name inside), and bump `SETS = 3` to `4` in
  [`_includes/header_custom.html`](_includes/header_custom.html).
- **To drop the logo-cycling** and keep just light/dark, remove the
  `logoLink` click handler in `_includes/header_custom.html`.

## Adding a page
Create a new file, name it
`something.md`, paste the template below, commit.

### A normal page

```markdown
---
title: Resources
nav_order: 6
permalink: /resources
---

# Resources

Your content here…
```

- **`title`** -- shown in the sidebar and the browser tab.
- **`nav_order`** -- position in the sidebar. 
- **`permalink`** -- the page's URL (`/resources`). Optional; without it the URL
  follows the filename.


### In-page table of contents

For a long page, add this just below the `# Heading` to get an auto-generated,
linked contents list (see the Policies and Staff pages):

```markdown
# Course Policies
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## First real section
…
```

`{: .no_toc }` on a heading will keep it out of that contents list.

### A section with sub-pages

For something that has its own child pages (e.g. an "Assignments" page):

**Parent** -- `assignments.md`:

```markdown
---
title: Assignments
nav_order: 4
has_children: true
permalink: /assignments
---

# Assignments

Overview. The individual assignments are listed under this item in the sidebar.
```

**Each child** -- e.g. `assignments/reflection-1.md` (you can use a subfolder to keep the repo
tidy; the folder name doesn't matter since the `parent:` value is what links them):

```markdown
---
title: Reflection 1
parent: Assignments
nav_order: 1
---

# Reflection 1
…
```

The child's `nav_order` orders it *within* that section. For a third level, a
grandchild adds `grand_parent: Assignments` and points `parent:` at the child.

### A sidebar link to an external site (no page)

Add to `_config.yml`:

```yaml
nav_external_links:
  - title: Feedback form
    url: https://forms.gle/…
```

### Other front-matter options

| Add this line | Effect |
|:--------------|:-------|
| `nav_exclude: true` | Page still works by URL, but is hidden from the sidebar |
| `search_exclude: true` | Keep the page out of site search  |

---

## Starting a new semester

`main` is always the current, live semester. At the end of a term you freeze the
old one on an `archive/…` branch, then update `main` for the new one.
Refer to [`ROLLOVER.md`](ROLLOVER.md) for a full checklist of config values, files etc. to change when rolling over the site.

---

## Previewing locally (optional)

Running the website locally allows you to preview the site as you make updates (without making commits). To do this, you'll need to install Ruby (`version >=3.1`) on your own device (look up the official guidelines for installing Ruby on your OS). 

(However, this may be annoying to do if you are on Windows. The official method seems to be to use RubyInstaller, but I personally use WSL2 as I couldn't get RubyInstaller to work. -Lydia) 


---

## Deployment (Github Pages ONLY)

~~[`.github/workflows/pages.yml`](.github/workflows/pages.yml) builds the site
with Jekyll on GitHub's servers on every push to `main`, and deploys it to
GitHub Pages once the `ENABLE_PAGES` variable is set (see "Publishing" above).
Check the **Actions** tab for build logs if a change doesn't show up.~~
