# Weather Radar Workshop — JupyterLite scaffold

A zero-install, browser-based home for the workshop notebooks. Participants open
one link and run everything in their browser — no Python, no accounts, no setup.
Works offline once loaded.

## Repository layout

    radar-workshop/
    ├── content/                    # your notebooks live here
    │   └── README.md
    ├── environment.yml             # YOUR local authoring env (JupyterLab)
    ├── requirements.txt            # build-time deps for the site
    ├── jupyter-lite.json           # optional site config
    └── .github/workflows/deploy.yml  # auto-build + publish to GitHub Pages

## One-time setup

1. Create a **public** GitHub repo and push these files to the `main` branch.
2. In the repo, go to **Settings → Pages → Build and deployment → Source**
   and select **GitHub Actions**.
3. That's it. Every push to `main` rebuilds and republishes the site.
   The live URL appears in the **Actions** run summary and under **Settings → Pages**,
   typically: `https://<your-username>.github.io/<repo-name>/`

## Authoring loop

```bash
conda env create -f environment.yml
conda activate radar-workshop
jupyter lab            # write/test notebooks in content/
git add . && git commit -m "update notebooks" && git push
```

Push, wait ~1–2 min for the Action to finish, refresh the live URL.

## Important: in-browser packages

The notebooks run on **Pyodide** in the browser, not your conda env. numpy,
scipy, matplotlib, pandas, and ipywidgets are all available. If you ever need a
package that isn't preloaded, add a first cell:

```python
%pip install -q some-pure-python-package
```

(only pure-Python `py3-none-any` wheels can be installed this way).

## Offline use

The build already produces a self-contained `dist/` folder. To hand it out
offline (USB stick or local network), grab the built site:

```bash
pip install -r requirements.txt
jupyter lite build --contents content --output-dir dist
# open dist/index.html, or serve the folder on a local network
```

Note: by default Pyodide's runtime is fetched from a CDN on first load. For a
**fully** offline build (no CDN at all), self-host Pyodide at build time:

```bash
jupyter lite build --contents content --output-dir dist \
  --pyodide https://github.com/pyodide/pyodide/releases/download/<version>/pyodide-<version>.tar.bz2
```

This makes `dist/` larger (~180 MB) but completely network-independent.
