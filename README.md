# Digital Composites with Reprogrammable Phase Architectures

This repository contains data supporting the published article:

> **Digital composites with reprogrammable phase architectures**  
> Yun Bai, Xuebo Yuan, Yang Weng, Kaiping Yin, and Xiaoyue Ni (2026).  
> *Science Advances*, 12(4), published 23 January 2026. https://doi.org/10.1126/sciadv.aed9698

## Related Work

This repository supports results published in:

> **Digital composites with reprogrammable phase architectures**  
> Yun Bai et al. (2026). *Science Advances*, 12(4), published 23 January 2026.  
> [Published article](https://doi.org/10.1126/sciadv.aed9698)

## Repository Contents

The repository contains the configuration matrix and statistical results generated for the study. All files are plain-text data files with whitespace-separated values and can be read with Python, MATLAB, R, or other scientific-computing tools.

| File | Description | Size |
| --- | --- | --- |
| `configuration.txt` | Configuration matrix. Each row contains 81 integer values describing one computational sample or state. | 60,475 rows x 81 columns |
| `results_DIC.txt` | DIC-related statistics for `vxy`, `vyx`, and the maximum principal strain `e1max`. | 60,475 data rows x 6 columns, plus a header |
| `results_dynmod.txt` | Dynamic-model results, including x/y-direction modulus, Poisson's ratio, and loss tangent statistics. | 60,475 data rows x 8 columns, plus a header |
| `results_eyd.txt` | Yield-related results, including the mean and standard deviation of the yield value. | 60,475 data rows x 2 columns, plus a header |

## Result Fields

### `results_DIC.txt`

- `vxy_mean`, `vxy_std`: mean and standard deviation of the Poisson's ratio `vxy`
- `vyx_mean`, `vyx_std`: mean and standard deviation of the Poisson's ratio `vyx`
- `e1max_mean`, `e1max_std`: mean and standard deviation of the maximum principal strain `e1max`

### `results_dynmod.txt`

- `Ex_mean`, `Ex_std`: mean and standard deviation of the x-direction modulus `Ex`
- `Ey_mean`, `Ey_std`: mean and standard deviation of the y-direction modulus `Ey`
- `lossx_mean`, `lossx_std`: mean and standard deviation of the x-direction loss tangent
- `lossy_mean`, `lossy_std`: mean and standard deviation of the y-direction loss tangent

### `results_eyd.txt`

- `yield_mean`: mean yield value
- `yield_std`: standard deviation of the yield value

## Reading the Data

```python
import numpy as np

configuration = np.loadtxt("configuration.txt", dtype=int)
results_dic = np.loadtxt("results_DIC.txt", skiprows=1)
results_dynmod = np.loadtxt("results_dynmod.txt", skiprows=1)
results_eyd = np.loadtxt("results_eyd.txt", skiprows=1)

print(configuration.shape)  # (60475, 81)
print(results_dic.shape)    # (60475, 6)
print(results_dynmod.shape) # (60475, 8)
print(results_eyd.shape)    # (60475, 2)
```

Rows correspond across files: row `n` in `configuration.txt` corresponds to record `n` in each results file. The first row of each results file contains column names and should be skipped when loading numerical data.

The repository currently contains data and documentation only; it does not include the scripts used to generate the results. The physical units and the detailed meaning of each configuration column should be confirmed against the published article and the associated model or experimental setup.

## Data and Code Availability

The complete raw datasets and the analysis code are available in the related [PM GitHub repository](https://github.com/ni-x-lab/PM). Run `download_data.py` in that repository to download the raw data used for the figures, including:

- `quasi-static_biaxial_test`: raw force-displacement data for Fig. 1
- `viscoelasticity_npy_int16`: raw force-displacement data for Fig. 2
- `plasticity_npy_int16`: raw force-displacement data for Fig. 3
- `program_stress_strain`: raw force-displacement data for Fig. 4
- `viscoelasticity_3D_npy_int16`: raw force-displacement data for Fig. 5
- `DIC_example`: example raw images and DIC results

The [Figshare archive](https://doi.org/10.6084/m9.figshare.29362844) provides an additional public copy of the source data and analysis code. This repository contains the processed configuration and results files described above.

## License

### Duke University Dual-Licensing Notice

The contents of this repository are owned by Duke University. Two licensing options are offered:

1. An open-source license under the [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](https://creativecommons.org/licenses/by-nc-nd/4.0/).
2. A custom license with Duke University for commercial use or any use not permitted under the CC BY-NC-ND 4.0 license.

Recipients may choose which license to receive the repository contents under. For uses outside the CC BY-NC-ND 4.0 restrictions, please contact Duke University to inquire about a custom license agreement.

This repository is distributed **AS IS**, without any warranty, express or implied.