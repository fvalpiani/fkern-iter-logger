# fkern-iter-logger

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18805060.svg)](https://doi.org/10.5281/zenodo.18805060)

Modified FEMM 4.2 magnetic solver that records the number of Newton-Raphson
iterations performed during an analysis.

This software was developed for the research presented in *Accelerating
Magnetostatic FEM Simulations of Electric Machines with Echo State Networks*.

## What is included

- `fkn.exe`: ready-to-use modified FEMM magnetic solver.
- `prob1big.cpp`: modified source file, included to make the changes
  inspectable. It is not a complete standalone FEMM build tree.
- `FV_example.FEM`: example FEMM problem used to test the modified
  solver.
- `FV_example.ans` and `FV_example.iter`: reference outputs
  produced by the supplied executable.

## Requirements

- Windows x64.
- The 64-bit version of FEMM 4.2 installed.

The supplied executable is 64-bit and must not be used with a 32-bit FEMM
installation.

## Installation

1. Close FEMM.
2. Open the FEMM installation folder and locate its existing `fkn.exe` file.
3. Make a backup of the original file, for example by renaming it to
   `fkn_original.exe`.
4. Copy `fkn.exe` from this repository into the same folder.

Depending on where FEMM is installed, Windows may request administrator
permission when replacing the file.

To restore the standard solver, delete the modified `fkn.exe` and rename the
backup to `fkn.exe`.

## Usage and verification

Use FEMM normally after installing the modified solver. For each successfully
completed magnetic analysis, an additional `.iter` file is written next to the
usual `.ans` result file.

To verify the installation:

1. Open `FV_example.FEM` in FEMM.
2. Run the analysis.
3. Check the `examples` folder for `FV_example.ans` and `FV_example.iter`.

With the supplied example and executable, `FV_example.iter` contains:

```text
28
```

## `.iter` file format

The file uses the same base name as the FEMM problem and contains one plain-text
integer: the total number of solver iterations performed to reach convergence.
It can be opened with any text editor or read directly from a script.

For example, an analysis of `model.FEM` produces:

```text
model.ans
model.iter
```

## Citation

If you use this software in your research, please cite the archived release:

```bibtex
@software{valpiani2026fkern,
  author    = {Federico Valpiani},
  title     = {fkern-iter-logger: Modified FEMM kernel with Newton-Raphson convergence logging},
  version   = {1.0.0},
  year      = {2026},
  publisher = {Zenodo},
  doi       = {10.5281/zenodo.18805060},
  url       = {https://doi.org/10.5281/zenodo.18805060}
}
```

The associated paper is:

```bibtex
@inproceedings{valpiani2026accelerating,
  title     = {Accelerating Magnetostatic FEM Simulations of Electric Machines with Echo State Networks},
  author    = {Valpiani, F. and Bramerdorfer, G. and Niccolai, A. and Leva, S.},
  booktitle = {27th International Conference on Electrical Machines (ICEM)},
  address   = {Madeira, Portugal},
  year      = {2026}
}
```

Machine-readable citation metadata are also available in `CITATION.cff`.

## License and acknowledgments

This repository is a derivative of FEMM 4.2 by David Meeker and is distributed
under the Aladdin Free Public License. See `LICENSE` and the
[official FEMM license page](https://www.femm.info/doku/doku.php?id=license).

The Newton-Raphson iteration logging modification is Copyright (C) 2026
Federico Valpiani.

## Contact

Federico Valpiani  
Department of Energy, Politecnico di Milano  
<federico.valpiani@polimi.it>  
[ORCID 0009-0004-8274-8094](https://orcid.org/0009-0004-8274-8094)
