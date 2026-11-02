# AC HUB starter

Skills for scholarly work with Claude Code, shared from Oskari Juurikkala's working
system. This is a pilot (version 0.1).

- **study** is a protocol for working through a source or a literature with Claude as
  a colleague: you choose how deep to go and which instruments to use (a sweep, an
  outline, a conversation, questioning, terms and names, close analysis). It keeps a
  store of what you found, a thinking note, and optional visual maps.

More is coming: a short account of the principles and architecture behind the system,
and later a source-conversion plugin (PDFs to citable markdown with the printed page
numbers kept).

You don't need to read the rest of this file yourself. **Open Claude Code in your
workspace folder and say: "Read the README at github.com/oskarijuurikkala/ac-hub-starter
and set me up, step by step."** Claude will do the steps and ask before installing
anything.

---

## Setup (for Claude, on a Mac)

Do these in order, telling the user what each step is for and asking before each
install. Skip anything already present.

**1. Tools.** Check `brew --version`; if Homebrew is missing, give the user the
one-line installer from https://brew.sh to paste into Terminal themselves (it asks
for their Mac password, which Claude must not handle). Then:

```
brew install poppler node
```

Poppler lets Claude look at a PDF page as an image (needed when a page's text is
doubtful, and for Greek). Node runs the study plugin's checkers for its visual maps.

**2. The plugin.** In Claude Code:

```
/plugin marketplace add oskarijuurikkala/ac-hub-starter
/plugin install study@ac-hub-starter
```

Restart Claude Code so the skill loads.

**3. The profile.** Create `.claude/workbench-profile.md` in the user's workspace with
the content below. Ask the user for their name, where they keep their sources, and a
sentence on their fields; fill those in. Create the folders and the log file it names
if they don't exist.

```markdown
---
# Your workbench profile. The shared skills read this file for everything
# that is yours: your name and where your files live.
# Updates to the skills never touch it.
# Paths are relative to the workspace folder.

name: ""                      # how Claude refers to you, e.g. "Kenny"
library_root: "Library"       # where your sources (PDFs and their markdown) live
study_root: "Studies"         # where study stores, thinking notes and maps go
study_log: "_logs/study-log.md"
---

# Workbench profile

Anything you want Claude to know about how you work with sources can go below
in plain prose: your fields and where you are expert or new, the editions you rely
on, how you cite, the languages you read.
```

**4. A first study.** Ask the user for a source they want to work on (an article or a
chapter, ideally a PDF with a text layer, or markdown) and say: "study this". The
skill will ask what they want from it before doing anything. Its maps are HTML files
in the study folder; open one in the browser with `open "<file>.html"`.

---

## Updates

Oskari releases updates now and then, with a note in [CHANGELOG.md](CHANGELOG.md).
To fetch them: `/plugin marketplace update ac-hub-starter`, then restart. Claude Code
can also update a marketplace automatically (in `/plugin`, under the marketplace's
settings). Your profile, your logs and your study files are never touched by an
update: they live in your workspace, not in the plugin.

## When something goes wrong, or works well

Tell Oskari, or open an issue on this repository (Claude can draft it). Both kinds of
report are useful: what failed, and what you found yourself relying on.

## What this skill will not do

It doesn't write your prose. Everything Claude extracts from a source is a reading to
check, not a quotation to cite: verify it against the printed edition before it goes
into your work.

## License

© 2026 Oskari Juurikkala. Licensed under [Creative Commons Attribution 4.0
International (CC BY 4.0)](LICENSE): you may use, share and adapt this material,
including in your own skills, provided you credit the author and link to this
repository.
