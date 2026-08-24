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

These are image-only scans; `pdftotext` returns nothing for them. Descriptions were
written from the document images or, where the page images could not be extracted
with the tools available here, from the filename and surrounding context. Running
OCR on these would improve their descriptions and enable `object_transcript`:

- `AK_TWS_2019_ANWR_DEIS_Comments.pdf`
- `AK_TWS_2019_Ambler_Road_DEIS_Comments.pdf`
- `AK_TWS_2019_Tongass_Roadless_Rule_Comments.pdf`
- `AK_TWS_2019_Willow_DEIS_Comments.pdf`
- `AK_TWS_2020_NPRA_DEIS_Comments.pdf`

## Derivative images

`image_small` and `image_thumb` paths follow the existing convention
(`_sm.jpg` at 800×800 fit, `_th.jpg` at 450px wide).

- **Generated (44):** all `image/jpeg` objects, with EXIF orientation applied so
  sideways phone photographs of documents render upright.
- **Not generated (171):** PDF, Word, PowerPoint, RTF, text, and zip objects. These
  need a document rasterizer (ImageMagick + Ghostscript), which is not installed on
  this machine. Run `rake generate_derivatives` once those are available; the CSV
  paths are already correct and will resolve when the files appear.

## Pre-existing note

`aktws0031` was already absent from `_data/aktws-metadata.csv` before this ingest.
The gap was left as-is rather than renumbering existing records.
