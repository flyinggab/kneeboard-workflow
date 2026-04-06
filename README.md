# DCS Kneeboard Generator

Generate a single-page A4 kneeboard for any DCS World flight — no software to install,
no terminal needed. Everything runs in two browser tabs: Claude and Overleaf.

---

## What you need

- A free account on [claude.ai](https://claude.ai)
- A free account on [overleaf.com](https://overleaf.com)
- Your mission's PDF briefing **or** the extracted `mission` text file from the `.miz`

---

## One-time setup (do this once, then reuse forever)

### 1. Create a Claude Project

1. Go to [claude.ai](https://claude.ai) and log in.
2. In the left sidebar, click **Projects** → **New Project**.
3. Give it a name, e.g. `DCS Kneeboard`.

### 2. Add the project instructions

1. Inside your new Project, click **Project instructions** (or the settings/pencil icon).
2. Open the file `project-instructions.md` from this folder.
3. Copy the entire contents and paste them into the Project instructions box.
4. Save.

### 3. Upload the template

1. Still inside the Project, find the **Project knowledge** section.
2. Click **Add content** → **Upload files**.
3. Upload `kneeboard-template.tex` from this folder.

That's the setup done. You never need to repeat these steps for this project.

---

## Every mission — generating a kneeboard

### Step 1 — Start a conversation

Open your `DCS Kneeboard` Project and click **New conversation**.

Claude will ask you a set of questions. Answer all of them:
- Which flight / callsign is this for?
- Which divert airports? (name, TACAN, ILS frequency, runway headings, elevation)
- What is the tasking and how many phases?
- What threats are present?

### Step 2 — Provide the mission data

Upload one of the following in the same message as your answers (or right after):

**Option A — PDF briefing** (easiest): just attach the PDF the mission editor gave you.

**Option B — DCS mission file**: if you have access to the `.miz` file, you need to
extract the `mission` text file from it first. See [Extracting the mission file](#extracting-the-mission-file-from-a-miz) below.

### Step 3 — Get the LaTeX code

Claude will read the file, extract all the data, and output a complete LaTeX code block.

### Step 4 — Compile on Overleaf

1. Go to [overleaf.com](https://overleaf.com) and log in.
2. Click **New Project** → **Blank Project** → give it any name.
3. In the editor on the left, **select all** the default text and **delete** it.
4. **Paste** the code Claude gave you.
5. Click **Recompile** (green button, top left).
6. Once compiled, click the **download** icon (top left, next to the PDF preview)
   to download your kneeboard PDF.

### Step 5 — Load in DCS

Copy the downloaded PDF into your DCS kneeboard folder:
```
C:\Users\<yourname>\Saved Games\DCS\Kneeboard\
```
or into the mission-specific kneeboard folder if the mission editor set one up.

---

## If Overleaf shows an error

Copy the red error text from Overleaf, paste it back into the Claude conversation,
and say "fix this error". Claude will output a corrected file — replace the Overleaf
content and recompile.

---

## Extracting the mission file from a .miz

A `.miz` file is a ZIP archive. To get the `mission` text file out of it:

**On Windows (no extra software needed):**
1. Make a copy of the `.miz` file.
2. Rename the copy so its extension is `.zip` (e.g. `my-mission.zip`).
3. Right-click → **Extract All**.
4. Open the extracted folder and find the file named `mission` (no extension).
5. Upload that file to Claude.

**On Mac:**
1. Rename the `.miz` to `.zip`.
2. Double-click to extract.
3. Find and upload the `mission` file.

---

## Tips

- You can reuse the same Overleaf project: just replace the code and recompile.
- If you want kneeboards in a language other than English, just tell Claude at the start.
- You can ask Claude to adjust any detail (altitude format, extra waypoints, different
  threat wording) before it outputs the final code.
