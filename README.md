# LibreOffice Aligner

A bilingual text aligner extension for LibreOffice Calc, designed to import documents, align source and target segments manually, and export translation memory (TMX) files.

## Features

* **Dedicated Toolbar:** All tools required for the alignment workflow are easily accessible from the custom *Aligner* toolbar.
* **Keyboard Shortcuts:** Core alignment functions (aligning, splitting, merging, moving) are mapped to hotkeys for a fast, keyboard-driven workflow.
* **Multi-Format Import:** Extract text directly from spreadsheets (ODS, XLSX), structured data (CSV, TSV), and standard documents (ODT, DOCX, RTF, HTML, TXT).
* **Regex Highlighting:** Configurable regular expression matcher to highlight specific text strings, aiding visual alignment.
* **Visual Anchoring:** Light-green color coding establishes anchored rows to keep perfectly aligned segments locked in place.
* **Standardized Export:** Generates valid `.tmx` files with user-defined `segtype` attributes.
  <img height="500" alt="image" src="https://github.com/user-attachments/assets/46b18ea1-0544-4c01-9e67-6a611b15e465" />


## Installation

1. Download the latest `.oxt` extension file from the [Releases](../../releases) page.
2. Open LibreOffice and navigate to **Tools > Extension Manager**.
3. Click **Add**, select the downloaded `.oxt` file, and accept the installation.
4. Restart LibreOffice. Open Calc, and the **Aligner** toolbar will appear.

## Usage

### 1. Importing Text
Start by populating column A (Source) and column B (Target).
* Use the **Import to Left Column** and **Import to Right Column** buttons on the toolbar, or simply paste your text manually.
* **Spreadsheets:** LibreOffice will prompt you to choose the target sheet and column.
* **CSV / TSV:** The standard text import dialog will appear, allowing you to configure delimiters for proper parsing.
* **Documents (ODT, DOCX, RTF, HTML, TXT):** Text is extracted and segmented strictly by paragraphs. No further automatic segmentation is applied during import.

### 2. Aligning Segments
* **Aligning Misaligned Segments:** If segments are out of sync, select the two corresponding cells in columns A and B, and press **Align and Anchor Segments**. The extension will automatically align them onto the same row and apply the anchor color.
* **Anchoring Aligned Segments:** If segments are already aligned on the same row but not yet anchored, select them and press **Apply Anchor Color** to lock them in place with a green background. Anchored rows serve as fixed points when shifting unaligned cells above or below them.
* **Splitting Segments:** To split a single cell's text into two segments, type the `||` delimiter at the desired split point and run the **Split Cell at Delimiter** command.
* **Regex Highlighting:** Use the custom regex feature to highlight tags, numbers, or specific terms to easily verify matches. The regex pattern and colors can be customized in the settings.
* **Formatting Cleanup:** Use **Reset Formatting** to remove all additional formatting (custom text colors and cell backgrounds) from either the currently selected region or the entire sheet.

### Keyboard Shortcuts
Most core alignment actions can be performed rapidly using the following default keyboard shortcuts:

| Shortcut | Action |
| :--- | :--- |
| `Ctrl` + `Alt` + `A` | Align and Anchor Segments |
| `Ctrl` + `Alt` + `Z` | Apply Anchor Color |
| `Ctrl` + `Alt` + `S` | Split Cell at Delimiter (`||`) |
| `Ctrl` + `Alt` + `M` | Merge with Cell Below |
| `Ctrl` + `Alt` + `,` | Move Segment Down |
| `Ctrl` + `Alt` + `.` | Move Segment Up |
| `Ctrl` + `Shift` + `-` | Remove Current Row |
| `Ctrl` + `Alt` + `0` | Reset Formatting |

### 3. Exporting to TMX
When your alignment is complete, use the export button to generate your translation memory.
* The first row of your spreadsheet must contain the language codes (e.g., `en-US`, `pl-PL`). The extension will check if they are present, but relies on the user to ensure the codes are formally valid.
* You will be prompted to select the `segtype` (e.g., `sentence` or `paragraph`) before the `.tmx` file is generated.

## Known Limitations

* **Regex Highlighting:** If a regular expression matches the *entire* content of a cell, the cell's background color will be highlighted rather than the text itself.
* **Segment Splitting:** Due to LibreOffice API limitations, segments cannot be split automatically at the current cursor/caret position. The `||` delimiter must be inserted manually before triggering the split command.
* **Document Segmentation:** Text documents are imported paragraph-by-paragraph. Sentence-level segmentation must be done manually or pre-processed prior to import.
* **Language Validation:** The TMX exporter checks for the existence of language headers but does not strictly validate ISO language codes.

## Acknowledgments

* This extension was developed as part of the ongoing language technology initiatives at [cApStAn](https://www.capstan.be/). <br>
  <img height="100" alt="cApStAn LQC" src="https://github.com/user-attachments/assets/1b10e75d-351b-42c6-a132-4a3465b2793f" />

* The icons used in the toolbar are part of the [Oxygen icon theme](https://github.com/KDE/oxygen-icons) for LibreOffice.
* The main icon for the extension is based on the Compare File Icon from [UXWing](https://uxwing.com).
