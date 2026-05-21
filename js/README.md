# Kiro Agent Hooks

Javscript specifc agent hooks (for now...)

## Agents

### 1. Generate Spec Tests

**Path:** `js/generate-spec-tests.kiro.hook`

**What it does:** Automatically generates comprehensive spec test files for all `.js` and `.mjs` files under `js/`. Tests are placed in a `tests/` directory mirroring the source folder structure (e.g., `js/lib/helpers.js` → `tests/lib/helpers.spec.js`). Skips files that already have a corresponding test.

**Trigger:** A `.js` or `.mjs` file is edited under `js/`.

**Pre-conditions:**
- Source files must be under the `js/` directory
- Existing test files will not be overwritten

---

### 2. Delete Spec Tests

**Path:** `js/delete-spec-tests.kiro.hook`

**What it does:** Automatically deletes the corresponding `.spec.js` (or `.test.js`) test file when a source JavaScript file is deleted. Does not act if the deleted file is itself a test file.

**Trigger:** A `.js` or `.mjs` file is deleted.

**Pre-conditions:**
- The deleted file must not itself be a test file
- A corresponding test file must exist in the `tests/` directory for any action to be taken

---

### 3. Sync Documentation

**Path:** `js/sync-documentation.kiro.hook`

**What it does:** Updates the `README.md` at the same directory level as the saved file to reflect any code changes, keeping documentation in sync with the codebase.

**Trigger:** Any `.js` file is edited.

**Pre-conditions:**
- A `README.md` must exist (or be creatable) at the same directory level as the edited file

---

### 4. Test Coverage Gap Report

**Path:** `js/test-coverage-report.kiro.hook`

**What it does:** After an agent task completes, scans all production JS/MJS files under `js/` and all test specs under `tests/`, then generates a timestamped markdown coverage report at `tests/reports/coverage-gap-report.<MM-dd-HH-mm>.md`. Old reports are deleted before writing the new one. The report includes summary metrics, untested/partially-tested function tables, and recommendations.

**Trigger:** An agent task stops (`agentStop` event).

**Limitations:**
- Coverage is approximate (static analysis, not runtime instrumentation)
- Only reports on exported/defined functions — internal closures may be missed
- Requires both `js/` and `tests/` directories to exist
- Previous reports in `tests/reports/` are deleted each run
