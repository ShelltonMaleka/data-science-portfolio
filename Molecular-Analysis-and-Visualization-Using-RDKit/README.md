# Molecular Analysis and Visualization Using RDKit

This project uses RDKit to explore molecular structures, extract atomic
information, visualize chemical compounds, and diagnose invalid SMILES strings.

It uses selected molecules from PubChem and the first six compounds in the
processed Delaney solubility dataset.

## Project Objectives

- Create RDKit molecules from SMILES representations.
- Count atoms and inspect their chemical symbols and atomic weights.
- Count aromatic bonds.
- Draw molecules in a labelled grid.
- Interpret RDKit parsing errors and propose valid SMILES corrections.

## Technologies Used

- Python
- RDKit
- pandas
- Jupyter Notebook

## 1. Molecular Information

The notebook examines the following molecules using SMILES representations
obtained from PubChem:

1. Propane
2. Ethene
3. Cyclohexane
4. Buckminsterfullerene

For each molecule, the analysis:

- Reports the number of atoms.
- Uses a loop to print each atom's chemical symbol and atomic weight.
- Reports the number of aromatic bonds.

RDKit generally represents hydrogen atoms implicitly when reading ordinary
SMILES strings. Atom counts should therefore state whether explicit
hydrogens have been added.

## 2. Drawing Molecules

The first six molecules in the Delaney dataset are converted from SMILES
into RDKit molecule objects.

The molecules are displayed in a grid with their `Compound ID` values
as labels.

## 3. Diagnosing SMILES Errors

The notebook investigates these invalid SMILES strings:

```text
CC(C
C1CCC
C(C)(C)(C)(C)C
```

RDKit's diagnostic messages are used to explain the parsing failures.
A separate Markdown answer discusses each error and proposes a valid
correction.

These corrections are possible alternatives; the intended molecular
structure cannot always be recovered from an invalid string.

## Dataset

The processed Delaney dataset contains molecular identifiers, SMILES
strings, molecular descriptors, and experimentally measured solubility.

This assignment uses:

- `Compound ID` for molecule labels.
- `smiles` to construct and draw molecular structures.

The solubility column is not used for predictive modelling in this project.

## Project Files

| File | Description |
|---|---|
| `RDKit_Molecular_Analysis.ipynb` | Molecular analysis, drawings, and error explanations |
| `solubility.csv` | Processed Delaney dataset |
| `README.md` | Project overview and running instructions |

## How to Run

### 1. Prepare the Files

Keep the notebook and dataset in the same folder.

If the downloaded dataset is named `solubility (1).csv`, rename it to
`solubility.csv` to match the notebook.

### 2. Install Dependencies

```bash
python -m pip install rdkit pandas notebook
```

### 3. Launch Jupyter Notebook

Run this command from the project folder:

```bash
python -m notebook
```

### 4. Run the Analysis

Open `RDKit_Molecular_Analysis.ipynb` and run the cells in order.

## Considerations

- Distinguish implicit hydrogen atoms from explicit atoms when reporting counts.
- Check whether SMILES parsing returns a valid molecule before analysing it.
- Use RDKit's aromaticity assignments when counting aromatic bonds.
- Keep diagnostic messages visible when investigating invalid SMILES.
- Adjust grid size and drawing dimensions to keep structures and labels readable.

## References

- [RDKit Documentation](https://www.rdkit.org/docs/)
- [PubChem](https://pubchem.ncbi.nlm.nih.gov/)
- Delaney, J. S. (2004). *ESOL: Estimating Aqueous Solubility Directly
  from Molecular Structure*. Journal of Chemical Information and Computer
  Sciences, 44(3), 1000–1005.

## Author

**Maleka Shellton**

GitHub: [ShelltonMaleka](https://github.com/ShelltonMaleka)# Molecular Analysis and Visualization Using RDKit

This project uses RDKit to explore molecular structures, extract atomic
information, visualize chemical compounds, and diagnose invalid SMILES strings.

It uses selected molecules from PubChem and the first six compounds in the
processed Delaney solubility dataset.

## Project Objectives

- Create RDKit molecules from SMILES representations.
- Count atoms and inspect their chemical symbols and atomic weights.
- Count aromatic bonds.
- Draw molecules in a labelled grid.
- Interpret RDKit parsing errors and propose valid SMILES corrections.

## Technologies Used

- Python
- RDKit
- pandas
- Jupyter Notebook

## 1. Molecular Information

The notebook examines the following molecules using SMILES representations
obtained from PubChem:

1. Propane
2. Ethene
3. Cyclohexane
4. Buckminsterfullerene

For each molecule, the analysis:

- Reports the number of atoms.
- Uses a loop to print each atom's chemical symbol and atomic weight.
- Reports the number of aromatic bonds.

RDKit generally represents hydrogen atoms implicitly when reading ordinary
SMILES strings. Atom counts should therefore state whether explicit
hydrogens have been added.

## 2. Drawing Molecules

The first six molecules in the Delaney dataset are converted from SMILES
into RDKit molecule objects.

The molecules are displayed in a grid with their `Compound ID` values
as labels.

## 3. Diagnosing SMILES Errors

The notebook investigates these invalid SMILES strings:

```text
CC(C
C1CCC
C(C)(C)(C)(C)C
```

RDKit's diagnostic messages are used to explain the parsing failures.
A separate Markdown answer discusses each error and proposes a valid
correction.

These corrections are possible alternatives; the intended molecular
structure cannot always be recovered from an invalid string.

## Dataset

The processed Delaney dataset contains molecular identifiers, SMILES
strings, molecular descriptors, and experimentally measured solubility.

This assignment uses:

- `Compound ID` for molecule labels.
- `smiles` to construct and draw molecular structures.

The solubility column is not used for predictive modelling in this project.

## Project Files

| File | Description |
|---|---|
| `RDKit_Molecular_Analysis.ipynb` | Molecular analysis, drawings, and error explanations |
| `solubility.csv` | Processed Delaney dataset |
| `README.md` | Project overview and running instructions |

## How to Run

### 1. Prepare the Files

Keep the notebook and dataset in the same folder.

If the downloaded dataset is named `solubility (1).csv`, rename it to
`solubility.csv` to match the notebook.

### 2. Install Dependencies

```bash
python -m pip install rdkit pandas notebook
```

### 3. Launch Jupyter Notebook

Run this command from the project folder:

```bash
python -m notebook
```

### 4. Run the Analysis

Open `RDKit_Molecular_Analysis.ipynb` and run the cells in order.

## Considerations

- Distinguish implicit hydrogen atoms from explicit atoms when reporting counts.
- Check whether SMILES parsing returns a valid molecule before analysing it.
- Use RDKit's aromaticity assignments when counting aromatic bonds.
- Keep diagnostic messages visible when investigating invalid SMILES.
- Adjust grid size and drawing dimensions to keep structures and labels readable.

## References

- [RDKit Documentation](https://www.rdkit.org/docs/)
- [PubChem](https://pubchem.ncbi.nlm.nih.gov/)
- Delaney, J. S. (2004). *ESOL: Estimating Aqueous Solubility Directly
  from Molecular Structure*. Journal of Chemical Information and Computer
  Sciences, 44(3), 1000–1005.
