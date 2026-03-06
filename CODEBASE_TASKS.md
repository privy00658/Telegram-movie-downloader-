# Codebase Issue Review: Proposed Tasks

## 1) Typo fix task
**Issue found:** The deployment section references `pxxl.app`, which appears to be a typo for **PaaS platform naming** and is inconsistent with common provider naming in docs.

**Task:** Correct the platform name typo in the deployment section and verify all references to external services are consistently spelled.

**Location:** `README.md` (deployment heading and related paragraph).

**Suggested acceptance criteria:**
- The deployment heading uses the correct platform name.
- No conflicting spellings remain in the README.

---

## 2) Bug fix task
**Issue found:** The merge instructions are presented under a `Windows:` label, but the command shown (`copy /b part_00+part_01 final.mp4`) is incomplete for multi-part files and does not mention ordering guarantees, which can produce corrupted output.

**Task:** Replace the current merge example with robust merge instructions for both Unix and Windows that correctly handle all generated chunks in order.

**Location:** `README.md` split/merge command examples.

**Suggested acceptance criteria:**
- Windows instructions include a method that supports all parts (not just two).
- Docs explicitly mention preserving part order.
- A short verification step (e.g., checksum or playable-file check) is documented.

---

## 3) Documentation discrepancy task
**Issue found:** The README claims broad functionality (download, format selection, splitting, sending, cleanup), but the repository currently contains documentation only and no implementation files (`main.py`, `requirements.txt`, bot handlers, etc.).

**Task:** Reconcile documentation with repository contents by either:
1. Adding the referenced implementation files, or
2. Clearly marking the README as a design/spec document and updating setup/run sections accordingly.

**Location:** Entire `README.md`, especially installation and run sections.

**Suggested acceptance criteria:**
- README does not claim runnable behavior unless matching source files exist.
- Setup instructions only reference files that are present in the repository.

---

## 4) Test improvement task
**Issue found:** There is no test suite or documentation linting, so command examples and file references can drift without detection.

**Task:** Add a lightweight CI check that validates README command blocks and referenced files.

**Suggested implementation idea:**
- Add a Markdown lint/check step (e.g., markdownlint or a custom script).
- Add a script that checks whether referenced files like `requirements.txt` and `main.py` exist when mentioned in runnable instructions.

**Suggested acceptance criteria:**
- CI fails when README references missing required files.
- CI fails on malformed command blocks in key sections.
- A local command to run these checks is documented.
