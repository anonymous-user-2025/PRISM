# PRISM: A multi-modal dataset for learning-based building performance modeling

This repository provides the supporting code for the **PRISM (Performance Representation Informed by Shape and Morphology)** dataset. It is a publicly available dataset that systematically links building geometry with high-fidelity simulation outputs across multiple environmental domains. PRISM features high morphological diversity, spanning basic extrusions to highly articulated forms; multi-modal geometric representations, including watertight surface meshes, signed distance fields and structured descriptors; and multi-physics simulation outputs from computational fluid dynamics (velocity, pressure) and solar exposure (sky view factor by sky patch). PRISM supports a wide range of research applications, including surrogate modeling, geometry-conditioned performance prediction, inverse design, generative modeling, and large-scale design-space exploration.

---

## Repository Contents

The repository contains tools for processing and visualization, morphology characterization, dataloader setups for direct integration with deep learning frameworks, and baseline implementations for learning-based surrogate modeling. It follows the following structure

```
PRISM/
├── src/
│   ├── prism/                  # dataset processing and visualization
│   ├── prism_morphology/       # morphology metrics 
│   └── prism_baselines/        # training loops, experiments, loaders
├── third_party/                
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
- Requirements are split into three files to facilitate selective use: 'requirements-dataset.txt' for the processing and visualization of the dataset, 'requirements-geometrics.txt' for the calculation of 3D shape metrics, and 'requirements-baselines.txt' for the baseline surrogate models.

## License

- **This repo:** see [LICENSE.md](./LICENSE.md)  
- **Third-party code:** see `third_party/licenses/`

---

## Citation

```
@misc{prism2025,
  title  = {PRISM: A multi-modal dataset for learning-based building performance modeling},
  author = {Anonymous},
  year   = {2025},
  url    = {https://dataverse.harvard.edu/previewurl.xhtml?token=57c1017c-2ff4-4b78-8f3e-4608b3ccb5ea}
}
```

