# MCDI505 — Análisis de series de tiempo

## Estructura

```text
mcdi505-analisis-series-tiempo/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   └── raw/
│       └── consumo_electrico_litoral.csv
├── notebooks/
│   └── mcdi505_s1lespinoza.ipynb
└── results/
    └── figures/
```

## Preparación

Desde la raíz del proyecto, crea y activa el entorno virtual (macOS/Linux):

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m ipykernel install --user --name mcdi505 --display-name "Python (MCDI505)"
```

Con el entorno activado, inicia JupyterLab:

```bash
jupyter lab
```

Abre `notebooks/mcdi505_s1lespinoza.ipynb` y selecciona el kernel **Python (MCDI505)** para desarrollar el análisis.

En sesiones posteriores, ejecuta `source .venv/bin/activate` y luego `jupyter lab`.
Los datos originales se guardan en `data/raw/` y las figuras en `results/figures/`.

### Compatibilidad con este Mac

Entorno validado con Python 3.10.4. Si SciPy falla al importar `_spropack`
con un error `__thread_bss` en macOS ARM64, instala el binario compatible:

```bash
python -m pip download --no-deps --only-binary=:all: --platform macosx_12_0_arm64 --dest /tmp/mcdi505-wheels scipy==1.15.3
python -m pip install --force-reinstall --no-deps /tmp/mcdi505-wheels/scipy-1.15.3-cp310-cp310-macosx_12_0_arm64.whl
```
