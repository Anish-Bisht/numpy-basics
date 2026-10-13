# NumPy Learning

A hands-on collection of Jupyter notebooks for learning NumPy, from creating arrays to analyzing restaurant sales and saving array data. Matplotlib is used for plotting and displaying images.

## Learning path

Work through the notebooks in this order:

| Notebook | Topics |
| --- | --- |
| [phase1-.ipynb](phase1-.ipynb) | Array creation, Python lists vs. NumPy arrays, vectors, matrices, tensors, array properties, reshaping, flattening, and transposing |
| [phase2.ipynb](phase2.ipynb) | Indexing, slicing, sorting, boolean masks, fancy indexing, `np.where`, concatenation, stacking, and deletion |
| [phase3.ipynb](phase3.ipynb) | Restaurant sales analysis, sums, minimums, maximums, averages, cumulative sums, plotting, vector arithmetic, dot products, and vector angles |
| [phase4.ipynb](phase4.ipynb) | Saving and loading `.npy` files and displaying an image with an inverted-color variant |

## Setup

Requires Python 3.12 or newer and [uv](https://docs.astral.sh/uv/).

From the project directory, install the dependencies declared in `pyproject.toml`:

```sh
uv sync
```

Launch JupyterLab with the project's Python environment:

```sh
uv run --with jupyterlab --with ipykernel jupyter lab
```

Open a notebook and run its cells from top to bottom. Start JupyterLab from the project directory so relative `.npy` paths resolve correctly.

## Restaurant sales example

The third notebook uses sample sales data for five restaurants from 2021 through 2024. Each row contains a restaurant ID followed by four annual sales values.

```python
import numpy as np

# Columns: restaurant_id, 2021, 2022, 2023, 2024
sales_data = np.array([
    [1, 150000, 180000, 220000, 250000],  # Paradise Biryani
    [2, 120000, 140000, 160000, 190000],  # Beijing Bites
    [3, 200000, 230000, 260000, 300000],  # Pizza Hub
    [4, 180000, 210000, 240000, 270000],  # Burger Point
    [5, 160000, 185000, 205000, 230000],  # Chai Point
])

sales = sales_data[:, 1:]  # Exclude restaurant IDs from calculations.
print("Total sales per year:", sales.sum(axis=0))
print("Total sales per restaurant:", sales.sum(axis=1))
```

For this two-dimensional sales array, `axis=0` combines restaurants for each year, and `axis=1` combines years for each restaurant.

## Data files

- `array1.npy`, `array2.npy`, and `array3.npy` are saved array examples. Running the save cells in `phase4.ipynb` overwrites these files; the current `array3.npy` save cell writes `array2`.
- `numpy-logo.npy` is the image array loaded by the fourth notebook.
- `main.py` is a starter script; the learning examples are in the notebooks.

These notebooks are learning exercises. The timing example in phase 1 compares different workloads, so it is not a reliable performance benchmark.
