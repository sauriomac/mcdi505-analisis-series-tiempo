# MCDI505 — Análisis de series de tiempo

## Estructura

```text
mcdi505-analisis-series-tiempo/
├── README.md
├── requirements.txt
├── .gitignore
├── data/raw/
│   ├── consumo_electrico_litoral.csv
│   └── consumo_electrico_litoral_depurado.csv
├── notebooks/
│   ├── notebook_formativa/
│   │   ├── mcdi505_s1lespinoza.ipynb
│   │   └── mcdi505_s2lespinoza.ipynb
│   └── notebooks_sumativa/
│       └── mcdi505_s1lespinoza.ipynb
└── results/figures/
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

Abre el notebook correspondiente dentro de `notebooks/notebook_formativa/` o `notebooks/notebooks_sumativa/` y selecciona el kernel **Python (MCDI505)** para desarrollar el análisis.

En sesiones posteriores, ejecuta `source .venv/bin/activate` y luego `jupyter lab`.
Los datos originales se guardan en `data/raw/` y las figuras en `results/figures/`.

### Compatibilidad con este Mac

Entorno validado con Python 3.10.4. Si SciPy falla al importar `_spropack`
con un error `__thread_bss` en macOS ARM64, instala el binario compatible:

```bash
python -m pip download --no-deps --only-binary=:all: --platform macosx_12_0_arm64 --dest /tmp/mcdi505-wheels scipy==1.15.3
python -m pip install --force-reinstall --no-deps /tmp/mcdi505-wheels/scipy-1.15.3-cp310-cp310-macosx_12_0_arm64.whl
```

## Formativa 02

Se agregó [Formativa 02 — Modelos clásicos (ARIMA/SARIMA)](notebooks/notebook_formativa/mcdi505_s2lespinoza.ipynb), con análisis de estacionariedad, comparación de modelos, validación temporal y diagnóstico de residuos.

- **Datos:** `data/raw/consumo_electrico_litoral_depurado.csv`, sin repetir imputaciones ni correcciones.
- **Partición:** entrenamiento 2015–2022 y validación 2023; 2024 queda reservado.
- **Reproducibilidad:** instrucciones en el notebook, dependencias en `requirements.txt`, registro de versiones y huella SHA-256 del CSV.
- **Figuras:** seis PNG en `results/figures/`, con prefijo `s2_`.
- **Ejecución comprobada:** macOS ARM64, Python 3.10.4; SciPy 1.15.3, statsmodels 0.14.5, pandas 2.3.3, NumPy 2.2.6 y Matplotlib 3.10.6. Las instrucciones para otros sistemas indican compatibilidad, sin presentarlas como plataformas probadas.

Selecciona **Python (MCDI505)** y ejecuta **Restart Kernel and Run All Cells**. Desde la raíz del proyecto, también puedes ejecutar:

```bash
source .venv/bin/activate
jupyter nbconvert --to notebook --execute --inplace --ExecutePreprocessor.kernel_name=mcdi505 --ExecutePreprocessor.timeout=180 notebooks/notebook_formativa/mcdi505_s2lespinoza.ipynb
```
