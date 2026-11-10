# Reading the Radar

Interactive notebooks from the weather radar short course taught at Clouds4Africa (July 2026) by Sebastián Torres (CIWRO, University of Oklahoma).

The notebooks run in the browser with JupyterLite, so there is nothing to install:

https://sebastiantorr.github.io/Clouds4Africa/

The first notebook can take 30–60 seconds to start while the browser loads Python.

## Notebooks

| File | Topic |
|---|---|
| `block1.ipynb` | The beam in space |
| `block2.ipynb` | One measurement |
| `block3.ipynb` | Range, velocity, and ambiguity |
| `block4.ipynb` | Wavelength, weather, and the scan |
| `block5.ipynb` | Two polarizations |
| `other/Explore_NEXRAD.ipynb` | Extra: exploring real NEXRAD data |

The slides and a reference sheet are in `content/materials/`.

## Running locally

```
conda env create -f environment.yml
conda activate radar-workshop
jupyter lab
```

The site is rebuilt from `content/` and published to GitHub Pages on every push to `main` (`.github/workflows/deploy.yml`).

## License

© 2026 Sebastián Torres. The notebooks, code and materials in this repository are licensed under the Creative Commons Attribution-NonCommercial 4.0 International License (CC BY-NC 4.0); see `LICENSE` or https://creativecommons.org/licenses/by-nc/4.0/.

Exceptions: the figure in `content/images/block4_image1.png` is courtesy of Alexander Ryzhkov (CIWRO, University of Oklahoma) and is not covered by this license. NOAA NEXRAD Level II data used in `Explore_NEXRAD.ipynb` are distributed by NOAA under its own terms.

## Contact

Sebastián Torres, sebas@ou.edu
