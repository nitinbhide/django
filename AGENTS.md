## Source and Documentation Index

The root `DOCMAP.md` and the cross-cutting maps are the preferred entry points for repository navigation. They are authoritative for high-level understanding and for deciding where to read source code and documentation.

Use the repository navigation maps (docmaps) in this order:

1. Start at `DOCMAP.md` for the repository overview, package entry points, and top-level navigation.
2. Read the cross-cutting maps to understand capability, architecture, technology, testing, and change-impact before drilling into implementation:
   - `FEATURE_MAP.md`
   - `ARCHITECTURE_MAP.md`
   - `TECHNOLOGY_MAP.md`
   - `TESTING_MAP.md`
   - `CHANGE_IMPACT_MAP.md`
3. Then read the authoritative folder-level `docmap.md` files under the relevant package or app folder.
4. Only read source files after narrowing to the right module or feature area.

## Primary File Selection Must Be Docmaps-Driven

Determine file relevance exclusively from DOCMAPS during primary selection. DOCMAPS are the authoritative descriptions of file purpose, and file selection must be based on their entries. Do not infer relevance from filenames, directory structure, or keyword similarity during primary selection.

## Heuristic Scanning as a Secondary Fallback

Heuristic scanning (grep, find, ripgrep, keyword search, symbol search, or directory traversal) is allowed only if DOCMAPS select zero candidate files and the task cannot proceed without identifying relevant files. Declare this fallback explicitly, justify the selected files, re-evaluate them against DOCMAPS when applicable, and discard any candidates that contradict DOCMAPS.

## File-Selection Justification

Before modifying files, provide a section titled `FILE SELECTION JUSTIFICATION`. For each candidate, quote its DOCMAPS entry and explain its relevance, or explain the fallback reasoning if DOCMAPS selected no files. Modify only the files selected and justified in that section.

## Self-Verification

Before reporting completion, verify that DOCMAPS were the primary decision source, heuristic scanning was used only under the fallback conditions, every selected file has valid justification, and no implicit or unjustified file access occurred. If neither DOCMAPS nor fallback scanning identify candidates, do not guess; request clarification.
