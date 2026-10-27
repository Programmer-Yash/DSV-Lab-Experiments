<div align="center">
<br/>

<img src="https://img.shields.io/badge/Python-3-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/Jupyter-Notebooks-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter"/>
<img src="https://img.shields.io/badge/NumPy-Arrays-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy"/>
<img src="https://img.shields.io/badge/Pandas-DataFrames-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas"/>
<img src="https://img.shields.io/github/last-commit/Programmer-Yash/DSV-Lab-Experiments?style=for-the-badge&color=2dd4bf&labelColor=0b1020" alt="Last commit"/>

<img src="assets/divider.svg" width="100%" alt=""/>

**A hands-on lab journal for Data Science & Visualization (DSV):**
**from `age = 25` to indexed, label-aligned DataFrames, one notebook at a time.**

</div>

<br/>

## ✦ What's inside

Four Jupyter notebooks of solved lab assignments. Each one is a self-contained practice sheet that you can read top to bottom or run cell by cell. From Assignment 3 onward they are graded in tiers, **Section A (Easy) → B (Medium) → C (Hard)**, so the difficulty ramps up inside every file.

| # | Notebook | Focus | Open |
|:-:|:--|:--|:-:|
| **02** | [`Assignment2.ipynb`](Assignment2.ipynb) | Python fundamentals (types, f-strings, `is` vs `==`) and a long **NumPy practice sheet** | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Programmer-Yash/DSV-Lab-Experiments/blob/main/Assignment2.ipynb) |
| **03** | [`Assignment3.ipynb`](Assignment3.ipynb) | **Pandas `Series`**: labels, boolean filters, `NaN`s, index alignment | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Programmer-Yash/DSV-Lab-Experiments/blob/main/Assignment3.ipynb) |
| **04** | [`Assignment4.ipynb`](Assignment4.ipynb) | Combined **NumPy + Series** revision with seeded RNG, matrix maths and `fill_value` | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Programmer-Yash/DSV-Lab-Experiments/blob/main/Assignment4.ipynb) |
| **05** | [`Assignment5.ipynb`](Assignment5.ipynb) | **Pandas `DataFrame`**: build, select, add and delete columns, align on index | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Programmer-Yash/DSV-Lab-Experiments/blob/main/Assignment5.ipynb) |

<br/>

## ✦ Peek inside each notebook

<details>
<summary><b>🧮 &nbsp;Assignment 2 · Python basics + NumPy</b> &nbsp;<sub>(click to expand)</sub></summary>

<br/>

**Warm-up:** variable types, dynamic typing (`x = 5` → `x = "five"`), string cleanup (`.strip()`, `.title()`), `list == list` vs `list is list`.

**NumPy sheet (Q1 → 30+):**

| Topic | What's practised |
|:--|:--|
| Creating arrays | `array`, `arange`, `linspace`, `zeros`, `reshape` |
| Math | element-wise ops, `square`, `sqrt`, `exp`, `maximum`, `minimum` |
| Indexing & slicing | `arr[:5]`, `arr[::-1]`, 2-D slices, **views vs `.copy()`** |
| Linear algebra | transpose `.T`, `np.dot`, matrix products |
| Conditional logic | `np.where` for pass/fail and High/Low income labels |
| Statistics | `sum`, `mean`, `var`, `std`, with `axis=0/1` |
| Sets & search | `any`, `all`, `sort`, `unique`, membership tests |

```python
marks   = np.array([[78, 85, 90], [45, 50, 55], [30, 40, 35]])
average = np.mean(marks, axis=1)          # one average per student
qualified = np.where(average >= 50)       # who passes?
```

</details>

<details>
<summary><b>🏷️ &nbsp;Assignment 3 · Pandas Series</b></summary>

<br/>

Three tiers of Series drills covering creation from lists and dicts, custom indexes, `.values` / `.index`, boolean masks, `in` checks, and `to_dict()`. The real star is **index alignment**: Pandas adds values by *label*, not by position, and labels that exist on only one side become `NaN`.

```python
s1 = Series({'A': 12, 'B': 18})
s2 = Series({'B': 5,  'C': 9})
print(s1 + s2)
# A     NaN
# B    23.0
# C     NaN
```

</details>

<details>
<summary><b>🔁 &nbsp;Assignment 4 · NumPy + Series revision</b></summary>

<br/>

Everything from the first three assignments, pushed harder.

- **NumPy:** `np.full`, `linspace`, fancy slicing, a `6×6` grid with sub-matrix means, billing with `quantity * price`, plus **reproducible randomness** via `default_rng(42)` and a 12×4 marks matrix analysed per student and per test.
- **Pandas:** multi-branch quarterly sales added together, `Index.intersection`, and the fix for missing data: `fill_value`.

```python
# Plain "+" turns a missing quarter into NaN; .add(..., fill_value=0) treats it as zero
filled = branch_a.add(branch_b, fill_value=0).add(branch_c, fill_value=0)
```

</details>

<details>
<summary><b>🧱 &nbsp;Assignment 5 · DataFrames</b></summary>

<br/>

Building tables from dicts of lists, selecting one column (`df.Name`, `df['City']`) vs several (`df[['Name','City']]`), and the many ways to add a column: a scalar, an `np.arange`, or a **Series that aligns on the index**. Columns come out again with `del`.

```python
office_names = pd.Series(['Delhi', 'Mumbai', 'Pune'], index=[0, 2, 4])
employee_df['Office'] = office_names      # rows 1 and 3 get NaN
```

</details>

<br/>

## ✦ Axis, finally clear

The single most useful idea across these notebooks, since it shows up in Assignments 2 and 4, is the `axis` argument. **`axis=1` runs across the columns and gives one result per row; `axis=0` runs down the rows and gives one result per column.**

## ✦ Cheat sheet from the labs

| Idea | Snippet | Why it matters |
|:--|:--|:--|
| View vs copy | `arr[0:5].copy()` | Slices are *views*; editing them edits the original |
| Reverse | `arr[::-1]` | Slicing with a negative step |
| Replace by rule | `np.where(marks < 40, 0, marks)` | Vectorised `if / else`, no loops |
| Missing labels | `Series(d, index=labels)` | Labels not in the dict become `NaN` |
| Detect gaps | `pd.isnull(s)` / `pd.notnull(s)` | Boolean masks for missing data |
| Safe addition | `a.add(b, fill_value=0)` | Treat "absent" as zero instead of `NaN` |
| Reproducible RNG | `np.random.default_rng(42)` | Same "random" numbers every run |
| Column from Series | `df['col'] = pd.Series(..., index=[...])` | Aligns on index, not position |

<img src="assets/divider.svg" width="100%" alt=""/>

## ✦ Run it yourself

```bash
# 1. clone
git clone https://github.com/Programmer-Yash/DSV-Lab-Experiments.git
cd DSV-Lab-Experiments

# 2. (optional) isolated environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 3. install what the notebooks use
pip install numpy pandas jupyter

# 4. launch
jupyter notebook
```

Prefer zero setup? Use the **Colab** buttons in the table above.

<br/>

## ✦ Repository map

```text
DSV-Lab-Experiments/
├── Assignment2.ipynb    # Python basics + NumPy practice sheet
├── Assignment3.ipynb    # Pandas Series (Easy / Medium / Hard)
├── Assignment4.ipynb    # NumPy + Series revision (Easy / Medium / Hard)
├── Assignment5.ipynb    # DataFrames (Easy / Medium / Hard)
└── README.md
```

<br/>

## ✦ What's next

- [x] Python fundamentals and NumPy
- [x] Pandas `Series`
- [x] Pandas `DataFrame` basics
- [ ] Row selection with `.loc` / `.iloc`
- [ ] Reading real data with `read_csv`, plus cleaning and `groupby`
- [ ] Plotting with Matplotlib / Seaborn: the **V** in DSV

<br/>

<div align="center">
<br/>

Made by **[Yash Upadhyay](https://github.com/Programmer-Yash)**

<sub>If these notebooks helped you, a ⭐ on the repo is always appreciated.</sub>

</div>
