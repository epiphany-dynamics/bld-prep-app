# Field Prep Sheet Automation

A local-first document workflow for turning inspection spreadsheets into structured prep sheets and print-ready PDFs.

This repository is a sanitized public example of the kind of document extraction and field-operations tooling Epiphany Dynamics builds. The original client inputs, branding, reference forms, and deployment configuration are intentionally excluded.

## What it demonstrates

- Spreadsheet ingestion for `.xlsx`, `.xls`, and `.csv` files
- Header detection and column mapping into a typed project model
- Segment-level editing with observations, notes, and a visual annotation layer
- Browser-local persistence with IndexedDB via Dexie
- PDF generation, combined batch export, and ZIP export with jsPDF and JSZip
- A small Astro shell around a React workflow UI
- A privacy-preserving architecture with no backend, login, API key, or external data store

The same pipeline can be extended with OCR when source documents are scans or image-based PDFs: OCR supplies extracted text, and the mapping/editor/export layers remain the same.

## Run it locally

Requirements: Node.js 22.12 or newer and npm.

```sh
npm install
npm run dev
```

Open the local URL printed by Astro, then upload the synthetic fixture at [`examples/inspection-sample.csv`](examples/inspection-sample.csv). The fixture contains invented values only.

Build the production bundle with:

```sh
npm run build
```

## Workflow

1. Upload an inspection spreadsheet or CSV.
2. Review the detected columns and map them to the prep-sheet fields.
3. Edit segment details and add annotations to the schematic.
4. Export one PDF, a combined PDF, or a ZIP of individual PDFs.
5. Keep the project in the browser's local IndexedDB store for later editing.

## Privacy and security

The public repository contains no credentials, tokens, private keys, client spreadsheets, populated inspection PDFs, or client branding. The app runs in the browser and does not include a server-side upload path.

Do not upload live customer, location, asset, or inspection data to a public demo. See [`SECURITY.md`](SECURITY.md) for reporting guidance.

## Case study: from spreadsheet to field-ready output

A field-services workflow that began with a spreadsheet and a paper-oriented form was reduced to one repeatable browser flow. Instead of manually copying rows, finding the right segment, sketching notes, and rebuilding a PDF, the operator can import the source file, validate the mapping, annotate the segment, and export the finished packet from one workspace.

The important engineering choice is not the PDF drawing code by itself. It is the typed intermediate model between messy source documents and deterministic output. That boundary makes the workflow testable, gives operators a review step before export, and creates a clean seam for adding OCR later.

### Outcome

- Less copy-and-paste between source spreadsheets and prep sheets
- A visible review step before a field packet is generated
- Repeatable output for single jobs and batches
- Local-first handling of operational data
- A reusable extraction-to-output pattern for future OCR projects

## Stack

Astro, React, TypeScript, SheetJS, Dexie, Konva, jsPDF, JSZip, and Leaflet.

## License

No open-source license has been added. Until a license is published, the source is available for inspection but is not granted for redistribution or commercial reuse.
