# Historical Documents ingest — 24 August 2026

Added `aktws0040`–`aktws0254` (215 items) to `_data/aktws-metadata.csv` from the
`Historical Documents/` folder. Files were copied to `objects/` using lowercased,
underscore-sanitized filenames matching the existing identifier convention.

## Source inventory

| | Count |
|---|---|
| Files in `Historical Documents/` | 314 |
| Already in the archive (aktws0001–aktws0039) | 37 |
| Excluded as duplicates or unusable | 62 |
| **Catalogued (aktws0040–aktws0254)** | **215** |

Date range 1968–2024. Earliest item is a 1968 National Wildlife Federation
wilderness-criteria memorandum; the earliest Chapter material is the 1971 charter
member record and the December 1974 Chapter newsletter.

## Exclusions

**Already archived (37).** Every PDF in `Historical Documents/Correspondence/` was
already present in `objects/` and catalogued as aktws0001–aktws0038 (verified by
MD5 hash).

**Byte-identical duplicates (21).**
- 20 newsletters in `Historical docs from Tom Paragi/` duplicate the copies in
  `Newsletters/`; the `Newsletters/` copy was kept.
- `AK_TWS_2019_MOVI_Disease_Position_Statement.pdf` is byte-identical to
  `AK_TWS_2013_Disease_Risk_Sheep_Position_Statement.pdf`; the 2013 filename was kept.

**Same document, different file (14).**
- `2004 NE NPR-A TWS comments Tom Franklin.pdf`, `AK-TWS_comments_NE_NPRA_2005.pdf`,
  and `comments 2007 Tanana Lakes.pdf` duplicate correspondence already archived.
- Two of the three copies of the 2019 Ambler Road DEIS comments.
- `D-2 Weeden Evenden 1971.JPG`, `D-2 Weeden Evenden 1971b true.JPG`, and
  `D-2 Weeden Evenden 1971c.JPG` are lower-resolution re-saves of
  `Weeden comments ANCSA to TWS Council 1971a/b/c.JPG` (kept).
- `Weeden comments ANCSA to TWS Council 1971.JPG` is a blurred phone photo of the
  document scanned cleanly as `D-2 Weeden 1971 notes.JPG` (kept).
- `D-2 Weeden LeResche 1974.JPG` is byte-identical to `D-2 Weeden 1974.JPG`.
- `AK_TWS_2022_Correspondence_UAF.docx` and `AK_TWS_2009_Tribute_Meg_Hahr.doc` are
  Word sources of already-archived PDFs.
- `NWSection_LandTransferPS.docx(1)` is a browser-download copy of
  `NWSection_LandTransferPS.docx`.

**Zip containers whose contents are already loose in the folder (2).**
`Alaska ZendTo-FdEdzvNEp2pfZMuf.zip` and
`Weeden files TWS and AK Chapter 1971-1987.zip`. Also
`AK research natural areas_shapefiles (1).zip`, identical to the copy that was kept.

**Zero-byte files (4).** All four PDFs in
`Position Statements and Resolutions/2020-2029/2024 MCH IM Program/Agency Docs/`
are 0 bytes and contain no data:
`2012_mulchatna_interim_im_report.pdf`,
`2024 Feb_mulchatna_intensive_management_annual_report Feb 2024.pdf`,
`2024 Oct_spring_mch_intensive_management_memo.pdf`,
`AK_BOG_findings_March2011_11-188-bog.pdf`.
These need to be re-sourced if they are wanted in the archive.

## Cataloguing decisions

- **Multi-page scan sets** are catalogued one record per file, with the page noted
  in the title (e.g. "… , 24 August 1971 (page 2)"). Where the Paragi folder also
  contains a Word document wrapping the same scans, that document is catalogued
  separately as a compiled version.
- **Dates** use `YYYY-MM-DD` where a full date appears in the document and bare
  `YYYY` where only the year is known — matching the existing rows aktws0030 and
  aktws0032. One item with no date at all (`NWSection_LandTransferPS.docx`) is
  flagged `1900-01-01`.
- **Filename dates were corrected against document content** where they disagreed:
  `AK_TWS_2018_Newsletter_Dec.pdf` is the Winter issue dated February 2018, and
  `TWS AK Chapter Newsletter-Winter 2014.pdf` is the January 2014 issue (distinct
  from the March 2014 Winter issue in `Newsletters/`).
- **Creator** is the named author where the document states one, otherwise `AKTWS`.
  76 of the 215 records carry a named creator.
- **Location** is filled only where the document itself names a place of origin
  (52 records).

## Items with no searchable text layer

These five are image-only scans; `pdftotext` returns nothing for them. Their page
images were read directly to write the metadata, so titles, dates, addressees, and
descriptions are taken from the documents themselves. Running OCR would still be
worthwhile to make them full-text searchable and to populate `object_transcript`:

- `AK_TWS_2019_ANWR_DEIS_Comments.pdf` — 12 Mar 2019, to Acting Sec. David Bernhardt
- `AK_TWS_2019_Ambler_Road_DEIS_Comments.pdf` — 24 Oct 2019, to Tina McMaster-Goering, BLM
- `AK_TWS_2019_Willow_DEIS_Comments.pdf` — 24 Oct 2019, to Sec. David Bernhardt
- `AK_TWS_2019_Tongass_Roadless_Rule_Comments.pdf` — 10 Dec 2019, to Sec. Sonny Perdue, USDA
- `AK_TWS_2020_NPRA_DEIS_Comments.pdf` — 17 Jan 2020, to Sec. David Bernhardt

## Derivative images

`image_small` and `image_thumb` paths follow the existing convention
(`_sm.jpg` at 800×800 fit, `_th.jpg` at 450px wide).

**Generated: 252 of 253 rows.** Neither Ruby, ImageMagick, nor Ghostscript was
installed. Page rendering used Windows' built-in `Windows.Data.Pdf` renderer plus
`System.Drawing`, driven from PowerShell, which needs no admin rights.

- 44 `image/jpeg` objects, with EXIF orientation applied so sideways phone
  photographs of documents render upright.
- 124 `application/pdf` objects, rendered from page 1 at 1600px and downsampled.
- 46 office documents (24 `.docx`, 17 `.doc`, 2 `.ppt`, 2 `.rtf`, 1 `.txt`),
  converted to a temporary PDF with LibreOffice in headless mode and then rendered
  the same way. Spot-checked across all four format families; text documents,
  the plain-text email, the PowerPoint title slide, and the scanned-page Word
  wrappers all render correctly.
- 38 objects that already had derivatives before this ingest.

**Not generated: 1 row** — `ak_research_natural_areas_shapefiles.zip`, which has no
renderable first page. CollectionBuilder shows a format-based icon for it.

Note that `rake generate_derivatives` would not have covered the office documents
either: its `EXTNAME_TYPE_MAP` handles only `.jpg`, `.jpeg`, `.png`, `.tif`,
`.tiff`, and `.pdf`, so those formats have always been outside its scope.

### Reproducing this

Two scripts in the session scratchpad do the work: `pdf_derivs.ps1` (images and
PDFs, no dependencies) and `lo_derivs.ps1` (office documents, takes a `-Soffice`
path). Both skip objects whose derivatives already exist, so they are safe to
re-run when new material is added.

LibreOffice was used portable, from a user-writable folder — its MSI is
machine-scope only and `winget install --scope user` is not available for it, so a
normal install would require admin.

An earlier attempt to convert the office documents with Word/PowerPoint COM
automation was abandoned: Word opens the files correctly and reports accurate page
counts, but both `Document.ExportAsFixedFormat` and
`Document.SaveAs2(..., wdFormatPDF)` hang indefinitely on this machine. That is not
a printer or file-location problem — it persists with a local virtual printer set as
`ActivePrinter` and with all optional export parameters passed explicitly. Anyone
retrying this work should use LibreOffice rather than Word.

## Pre-existing note

`aktws0031` was already absent from `_data/aktws-metadata.csv` before this ingest.
The gap was left as-is rather than renumbering existing records.

---

# Addendum — `Historical Documents/Recent`, 24 August 2026

Added `aktws0255`–`aktws0260` (6 items), bringing the collection to **259 rows**.
All six are born-digital PDFs with intact text layers, so no OCR was needed and no
page images had to be read visually.

| objectid | Date | Item |
|---|---|---|
| aktws0255 | 2025-03-07 | BOG Proposal 101 — intensive management of Dall sheep |
| aktws0256 | 2025-03-07 | BOG Proposal 147 — importation of exotic species |
| aktws0257 | 2025-03-24 | BOG RC009 timing — Mulchatna Caribou Herd IM petition |
| aktws0258 | 2025-07-01 | NPR-A draft Integrated Activity Plan EA comments |
| aktws0259 | 2026-02-27 | Letter to TWS Council — Student Liaison voting rights |
| aktws0260 | 2026-03-20 | Tongass Land Management Plan revision scoping comments |

Checks run: no MD5 duplicates against existing objects, none internally, no
zero-byte files, no identifier or filename collisions. Derivatives generated for
all six with `pdf_derivs.ps1` (0 failures) at the standard 800×800-fit and
450px-wide sizes.

Named creators are taken from the signature block: Ryan Mollnow (President) on five,
Alex Lewis (President-Elect) on the NPR-A letter.

One filename carried a double extension — `…Tongass Forest Plan March 2026.docx.pdf`
— which would have produced the identifier `…_2026_docx`. `gen2.awk` now collapses a
trailing document extension left in the stem, so the identifier is
`akchapter_scoping_comments_tongass_forest_plan_march_2026`.
