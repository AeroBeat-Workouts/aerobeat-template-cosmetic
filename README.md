# AeroBeat Cosmetic Template

UGC cosmetics (accessories and apparel) for AeroBeat.

## 📋 Repository Details

*   **Type:** Cosmetics (Art)
*   **License:** **CC BY-NC 4.0**
*   **Dependencies:**
    *   `aerobeat-core` (Required foundation for shared socket/resource contracts)

## GodotEnv development flow

This repo uses the AeroBeat GodotEnv asset-package convention.

- Canonical dev/test manifest: `.testbed/addons.jsonc`
- Installed dev/test addons: `.testbed/addons/`
- GodotEnv cache: `.testbed/.addons/`
- Hidden workbench project: `.testbed/project.godot`
- Repo-local unit tests: `.testbed/tests/`

The repo root remains the package/published boundary for downstream consumers. Day-to-day development, import checks, and validation happen from the hidden `.testbed/` workbench using the pinned OpenClaw toolchain: Godot `4.6.2 stable standard`.

### Restore dev/test dependencies

From the repo root:

```bash
cd .testbed
godotenv addons install
```

That installs the pinned `aerobeat-core` foundation plus GUT into `.testbed/addons/`.

### Open the workbench

From the repo root:

```bash
godot --editor --path .testbed
```

Use this `.testbed/` project as the canonical direct-development and import-validation surface for cosmetic work.

### Import smoke check

From the repo root:

```bash
godot --headless --path .testbed --import
```

### Run unit tests

From the repo root:

```bash
godot --headless --path .testbed --script addons/gut/gut_cmdln.gd \
  -gdir=res://tests \
  -ginclude_subdirs \
  -gexit
```

## 📂 Structure

*   `assets/accessories/` - Hats, glasses, props, and other attachable items.
*   `assets/apparel/` - Clothing and other wearable cosmetics.

## Validation notes

- `.testbed/addons.jsonc` is the committed dev/test dependency contract.
- The manifest pins `aerobeat-core` to `v0.1.0` and GUT to `main`.
- Repo-local unit tests live under `.testbed/tests/`.
- This template is root-packaged (`subfolder: "/"`) and does not use a `.testbed/src` bridge; cosmetic assets stay under the repo root package boundary.

## Notes

- Use the hidden workbench to restore shared contracts and import/test cosmetic resources before consuming them elsewhere.
