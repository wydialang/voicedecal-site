# Semester rollover

##  Versioning

- **`main` is always the current, live semester.**
- **Each past semester is frozen on its own branch** (`archive/fa26`,
  `archive/sp27`, …). 
- This means that optionally, each archive branch can also be deployed.

Do the steps below **at the end of a semester, before editing anything for the
next one.**

---

## 1. Freeze the semester that's ending

```bash
git checkout main
git pull
git branch archive/fa26          # use the semester_short that's ending
git push origin archive/fa26
```

---

## 2. Set up the new semester on `main`

Work on `main` (edit on github.com is fine). Change these, then commit:

### `_config.yml`
- [ ] `semester:` → e.g. `"Spring 2027"`
- [ ] `semester_short:` → e.g. `"sp27"`
  *(updates the semester across the sidebar, the home-page subtitle, and the footer)*

### External links -- `_config.yml`
- [ ] `syllabus_url:` → new semester's syllabus doc
- [ ] `discord_url:` → valid invite link (make sure link isn't expired)
- [ ] `feedback_url`
- [ ] `absences_url`
- [ ] `extensions_url`


### Home page -- `index.md`
- [ ] Rewrite the intro paragraph if anything changed (meeting time, units…)

### Course schedule -- `_data/schedule.yml`
- [ ] Replace with the new semester's weeks (one YAML block each — see the
  format in `README.md`)
- [ ] Reset `current_week` to `1` in `_config.yml`

### Weekly Calendar -- `calendar.md`
- [ ] **Google Calendar**: make a new calendar for the semester and set it up according to the instructions in `README.md`


### Staff -- `_data/staff.yml` and `staff.md`
- [ ] `_data/staff.yml`: one block per facilitator (name, photo, bio, contact);
  drop each photo in `assets/images/`
- [ ] `staff.md`: faculty sponsor, contributors, and the contact table

### About -- `about.md`
- [ ] Update enrollment steps if needed

### Announcements
- [ ] Clear old entries in `_data/announcements.yml`
- [ ] `announcements_enabled:` in `_config.yml` -- `true` only if you'll post them

### Content not tied to a semester (leave alone unless redesigning)
- theme colors (`_sass/color_schemes/`), logos (`assets/images/`),
  `_includes/`, `README.md`

---

## 3. Deploy
TODO

---

## Archived semesters

| Semester | Branch | Live at |
|:---------|:-------|:--------|
| _(none yet -- Fall 2026 is the first)_ | | |
