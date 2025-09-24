# PRISM: A multi-modal dataset for learning-based building performance modeling

This repository provides the supporting code for the **PRISM (Performance Representation Informed by Shape and Morphology)** dataset. It is a publicly available dataset that systematically links building geometry with high-fidelity simulation outputs across multiple environmental domains. PRISM features high morphological diversity, spanning basic extrusions to highly articulated forms; multi-modal geometric representations, including watertight surface meshes, signed distance fields and structured descriptors; and multi-physics simulation outputs from computational fluid dynamics (velocity, pressure) and solar exposure (sky view factor by sky patch). PRISM supports a wide range of research applications, including surrogate modeling, geometry-conditioned performance prediction, inverse design, generative modeling, and large-scale design-space exploration.
It contains tools for processing and visualization, morphology characterization, dataloader setups for direct integration with deep learning frameworks, and baseline implementations for learning-based surrogate modeling.

---

## Repository Layout

```
PRISM/
├── src/
│   ├── prism/                  # dataset processing (VTK→NPY, rotate/stats, subsample, viz)
│   ├── prism_morphology/       # morphology metrics scripts
│   └── prism_baselines/        # training loops, experiments, loaders
├── third_party/                # git submodules (unmodified)
│   ├── neural_solver_library/
│   └── 3d_building_metrics/
├── requirements-dataset.txt
├── requirements-geometrics.txt
├── requirements-baselines.txt
├── LICENSE.md
├── UPSTREAM.md
└── README.md
```

- All **our code** lives under `src/`
- **Third-party repos** are tracked as submodules in `third_party/`  
- Requirements are split into three files

---

## Cloning

Clone with submodules:

```bash
git clone --recurse-submodules https://github.com/<YOUR_ORG_OR_USER>/PRISM.git
cd PRISM
```

If you forgot `--recurse-submodules`:

```bash
git submodule update --init --recursive
```

---

## Installation

We recommend separate environments:

**Dataset / processing**
```bash
python -m venv .venv-data
source .venv-data/bin/activate
pip install -r requirements-dataset.txt
```

**Geometry metrics**
```bash
python -m venv .venv-geo
source .venv-geo/bin/activate
pip install -r requirements-geometrics.txt
```

**Baselines**
```bash
python -m venv .venv-base
source .venv-base/bin/activate
pip install -r requirements-baselines.txt
```

---

## Usage

### 1. Convert VTK/OBJ → NPY
```bash
python src/prism/processing/vtk_to_npy.py --data_dir /path/to/vtk_root
```

### 2. Compute Morphology Metrics
```bash
python src/prism_morphology/calc_geo_shape_metrics.py   --geo_dir /path/to/geometry   --density_3d 1   --density_2d 1
```

### 3. Train Baselines
```bash
python src/prism_baselines/run.py   --model GraphSAGE   --data_path /path/to/processed   --save_name graphsage_buildings
```

---

## Submodules

- `third_party/neural_solver_library` – upstream neural baselines  
- `third_party/3d_building_metrics` – upstream geometry metrics  

Exact versions and licenses are tracked in [UPSTREAM.md](./UPSTREAM.md).  
Update submodules with:

```bash
git submodule update --remote --merge
```

---

## License

- **This repo:** see [LICENSE.md](./LICENSE.md)  
- **Third-party code:** see `third_party/licenses/`

---

## Citation

```
@misc{prism2025,
  title  = {PRISM: Processing, Morphology & Baselines for Urban CFD},
  author = {Anonymous},
  year   = {2025},
  url    = {https://github.com/<YOUR_ORG_OR_USER>/PRISM}
}
```
