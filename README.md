# Molecular-dynamics workflow notes and input fragments

This is a chapter-organized archive of commands, topology fragments, and workflow notes for polymer/cosolvent molecular dynamics. The `.txt` files combine multiple syntaxes and are not directly executable shell programs.

## Functions and engineering applications

| Files | Observed content | Inferred application |
|---|---|---|
| `Chapter2.txt` | PACKMOL water/methanol packing example and visualization command | Initializing mixture configurations [1] |
| `Chapter3.txt`, `Chapter4.txt` | Historical software setup, archives, and file operations | Reconstructing the original computing workflow |
| `Chapter5.txt`, `Chapter8.txt` | GROMACS preprocessing, MPI/PBS execution, and loops | Composition/polymer simulation campaigns [2] |
| `Chapter6.txt`, `Chapter7.txt` | OPLS-style molecular topology and parameter fragments | Understanding organic-liquid force-field inputs [3] |
| `Chapter9.txt`, `Chapter10.txt` | Trajectory conversion, interface analysis, and plotting snippets | Studying surface activity and comparing solvent environments [4] |

## Example commands

After extracting only the PACKMOL input block from `Chapter2.txt` into a new `mixture.inp` file and supplying the referenced `water.pdb` and `methanol.pdb` structures:

```bash
packmol < mixture.inp
```

The recorded example specifies 2,207 water and 576 methanol molecules in a 60-by-60-by-70 box and writes `MeOHMix40.pdb`. Check PACKMOL length units and the intended mixture composition rather than inferring mass fraction from the filename.

For an existing trajectory and run-input file, a legacy analysis command has the form:

```bash
trjconv -f md_concat.trr -s md1.tpr -o md_out.gro
```

Select the intended group interactively. Inputs are external; the historical command is for a compatible GROMACS 4.x environment. To view an existing two-column analysis file in gnuplot:

```gnuplot
set datafile commentschars "#@&"
plot "density_z.xvg" using 1:2 with lines
```

`density_z.xvg` is an example user-supplied output file, not a bundled dataset. These are workflow examples, not a tested end-to-end installation.

## Reproducibility and citation corrections

Do not run a chapter with `bash Chapter5.txt`: prompt markers (`>`), explanatory prose, PBS directives, topology sections, and incomplete placeholders must first be separated. Historical installation instructions and large `-maxwarn` values should not be carried forward blindly. Missing molecular structures, production trajectories, force-field files, and scheduler configuration prevent automatic reproduction.

The earlier README listed the Polymer paper as 2025 and included a placeholder Zenodo DOI. The verified journal year is **2016** [4]; no software DOI is asserted here. The metadata file present is `Citation.cff` (that exact capitalization); review its metadata before relying on it. Cite the repository URL and commit as well as the relevant publications.

## Review scope and software citation

Documentation reviewed on 2026-10-08 against source commit [`9771e0aa8566`](https://github.com/gmongell/MolecularDynamicsSimulations_Bash/tree/9771e0aa8566775c068acfdbe140233f72d00ad0). “Observed” means supported by source inspection; engineering applications are reasoned possibilities unless explicitly demonstrated. Scholarly references provide methodological context and do not certify these implementations. Runtime validation is stated separately above.

For software attribution, cite Guy Francis Mongelli, *MolecularDynamicsSimulations_Bash*, the [repository](https://github.com/gmongell/MolecularDynamicsSimulations_Bash), the exact commit used, and your access date. Also cite the relevant method publications and any original third-party contributors. No unverified software DOI or release version is assigned by this documentation.

## Scholarly references

1. L. Martínez, R. Andrade, E. G. Birgin, and J. M. Martínez (2009). “PACKMOL: A package for building initial configurations for molecular dynamics simulations.” *Journal of Computational Chemistry* 30, 2157–2164. [DOI: 10.1002/jcc.21224](https://doi.org/10.1002/jcc.21224). Supports molecular packing and initialization workflows.

2. M. J. Abraham et al. (2015). “GROMACS: High performance molecular simulations through multi-level parallelism from laptops to supercomputers.” *SoftwareX* 1–2, 19–25. [DOI: 10.1016/j.softx.2015.06.001](https://doi.org/10.1016/j.softx.2015.06.001). Background for the simulation and analysis ecosystem; this does not establish compatibility with the legacy scripts.

3. W. L. Jorgensen, D. S. Maxwell, and J. Tirado-Rives (1996). “Development and Testing of the OPLS All-Atom Force Field on Conformational Energetics and Properties of Organic Liquids.” *JACS* 118, 11225–11236. [DOI: 10.1021/ja9621760](https://doi.org/10.1021/ja9621760). Methodological context for organic-liquid force fields and torsional/nonbonded parameters.

4. “The surface activity of polymers in cosolvated systems determined from computational simulation.” *Polymer* (2016). [DOI: 10.1016/j.polymer.2015.11.003](https://doi.org/10.1016/j.polymer.2015.11.003). Related polymer/cosolvent surface-activity research. The publisher indexes the journal publication as 2016; the DOI contains 2015. Exact reproduction requires the original inputs and analysis conventions.

## Ownership and existing license notices

Copyright (c) 2025 Guy Francis Mongelli

The existing project notice declares Apache License 2.0 for project code. Documentation, prose, and figures are declared CC BY 4.0; notebook code cells are Apache-2.0 and narrative/figures CC BY 4.0. Preserve all file-level and third-party notices. This README update does not change ownership or licensing terms.


## Reproducibility, source verification, and contribution policy (2026-10-08)

- **Observed versus proposed:** The function inventory above describes inspected source where indicated. Engineering applications identified as *inferred* are potential uses, not verified features or validated performance claims.
- **Usage examples:** Treat the documented commands and calls as illustrative until the referenced source file, runtime version, dependencies, required input data, and working directory have been checked. Do not execute notebook fragments or batch-scheduler directives as standalone programs without adapting their context.
- **Scientific citations:** References above identify relevant governing methods and computational background; citing a publication does not imply that its algorithm is implemented in this repository or that the publication was authored by this repository owner.
- **Missing or null artifacts:** Empty, placeholder, missing, or non-executable source files must not be represented as functional implementations. Candidate restorations from personal archives require provenance, content comparison, license review, and explicit verification before committing code.
- **Access model:** This repository is publicly readable. Public visibility does not grant anonymous push rights; write access is controlled separately through repository collaborators, credentials, apps, deploy keys, and branch rules. This README is descriptive and does not itself enforce permissions.
