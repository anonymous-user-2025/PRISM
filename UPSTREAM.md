# UPSTREAM

This document tracks third-party code included in this repository under `third_party/`.  
We use **Git submodules** to reference upstream projects at specific commits for reproducibility.

## Contents

- [Submodules (sources, versions, licenses)](#submodules-sources-versions-licenses)
- [Local layout](#local-layout)
- [How to clone (with submodules)](#how-to-clone-with-submodules)
- [How to update a submodule](#how-to-update-a-submodule)
- [Policy on local modifications](#policy-on-local-modifications)
- [License notes](#license-notes)

---

## Submodules (sources, versions, licenses)

### 1) `third_party/neural_solver_library`
- **Upstream:** `https://github.com/<ORIGIN_ORG>/<ORIGIN_REPO>`  
- **Pinned commit (SHA):** `xxxxxxxx`  
- **License:** See `third_party/licenses/neural_solver_library_LICENSE` (copied verbatim from upstream).  
- **Local changes:** **None** — used as a pure dependency.  
- **Used by:** `src/prism_baselines/*` (training loops, model factory, utils).

### 2) `third_party/3d_building_metrics`
- **Upstream:** `https://github.com/<ORIGIN_ORG>/<ORIGIN_REPO>`  
- **Pinned commit (SHA):** `yyyyyyyy`  
- **License:** See `third_party/licenses/3d_building_metrics_LICENSE` (copied verbatim from upstream).  
- **Local changes:** **None** — used as a pure dependency.  
- **Used by:** `src/prism_morphology/*` and geometry-metric scripts.

> Replace the placeholder URLs and SHAs with the actual upstream repository links and commit hashes you are pinned to.  
> To find the SHA: `git -C third_party/<name> rev-parse HEAD`

---

## Local layout

```
third_party/
  neural_solver_library/      # submodule (no local edits)
  3d_building_metrics/        # submodule (no local edits)
third_party/licenses/
  neural_solver_library_LICENSE
  3d_building_metrics_LICENSE
```

---

## How to clone (with submodules)

If you didn’t clone yet:
```bash
git clone https://github.com/anonymous-user-2025/PRISM.git
cd PRISM
git submodule update --init --recursive
```

If you already cloned without submodules:
```bash
git submodule update --init --recursive
```

To refresh submodules to the pinned SHAs:
```bash
git submodule sync --recursive
git submodule update --init --recursive
```

---

## How to update a submodule

1) Enter the submodule and pick a commit/tag:
```bash
cd third_party/neural_solver_library
git fetch origin --tags
git checkout <new-tag-or-commit>
```

2) Go back to the root and record the new pointer:
```bash
cd ../../
git add third_party/neural_solver_library
git commit -m "Bump neural_solver_library to <tag/sha>"
```

3) Update the **Pinned commit (SHA)** in this file.

> If the upstream update changes APIs, adjust our code under `src/` accordingly and bump the relevant `requirements-*.txt` if needed.

---

## Policy on local modifications

- We aim to keep **no local edits** to submodules.  
- If we must patch upstream:
  - Prefer opening a PR upstream.
  - If a temporary patch is required, **do not** edit files directly inside `third_party/<name>`. Instead:
    - Create a minimal wrapper/adapter under `src/` and import from there, **or**
    - Keep a small patch file under `patches/<name>/` and document:
      - What changed
      - Why it was needed
      - A link to the upstream issue/PR
- Any deviation must be documented here under the corresponding submodule’s **Local changes** bullet.

---

## License notes

- Third-party licenses are copied verbatim into `third_party/licenses/`.
- This repository’s own license is in `LICENSE.md`.
- When redistributing, ensure license terms of upstream projects are respected (e.g., notices retained).


