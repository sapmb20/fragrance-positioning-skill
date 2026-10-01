# Editing an existing Google Doc

Edits always go in the user's existing file, so their link, sharing settings and version history stay intact. Creating a copy or a new file leaves the user with two versions and an unedited original.

## Option A: Google Docs connector (preferred)

If a Google Docs connector or API tool is available, use it:
1. Read the document and note its revision ID.
2. Build all insertions (in-text citations, page break, Works Cited paragraphs, hanging indent via paragraph style `indentFirstLine` / `indentStart`) in one batch, guarded with the revision ID.
3. Insert from the end of the document backwards so earlier positions don't shift.
4. Read the document again and confirm every insertion.

## Option B: Browser automation

When there's no connector but a browser tool is available and the user is signed in:

**Find the file.** Search Drive by course code, assignment number or topic. Students often have several Google accounts (personal and school); if the file isn't found, ask which account it's in. Don't guess between similar files, such as several "Untitled document" entries.

**Read it.** Google Docs renders to a canvas, so page-text tools often return nothing. From the document tab, fetch the plain-text export instead:
```js
await fetch('/document/d/<DOC_ID>/export?format=txt').then(r => r.text())
```
Long results may be truncated in the tool output; store the text in a variable and read it in slices.

**Add in-text citations with Find and replace** (Cmd/Ctrl+Shift+H):
- Anchor each replacement on a short phrase that appears **exactly once**. The dialog shows a "1 of 1" count; check it before clicking "Replace all".
- Replace `<phrase>` with `<phrase> (Citation)`.
- Type curly quotes (“ ”) directly so they match the document's smart quotes.
- Clear each field with Select All before typing the next phrase.

**Add the Works Cited page:**
1. Close the dialog. Move to the end of the document (Cmd/Ctrl+Down) and confirm the cursor is on an empty final paragraph in Normal text style.
2. Insert a page break (Cmd/Ctrl+Enter).
3. Center (Cmd/Ctrl+Shift+E), type "Works Cited", press Enter, then left-align (Cmd/Ctrl+Shift+L).
4. Type each entry, toggling italics (Cmd/Ctrl+I) around container titles. Press Enter between entries.
5. Select all the entries (Shift+click at the start of the first one), then go to Format → Align & indent → Indentation options → Special indent: Hanging, 0.5 → Apply.

**Verify.** Fetch the text export again and check that each citation appears exactly once in the right place. Take a screenshot of the Works Cited page to check italics and the hanging indent.

Tell the user that every change can be undone from File → Version history.
