# Intelligent Task Offloading in Vehicular Edge Computing

This repository contains the implementation of a multi-objective reinforcement learning framework for task offloading in Vehicular Edge Computing (VEC).

The proposed framework integrates:

- TD3 (Twin Delayed Deep Deterministic Policy Gradient)
- NOMA-based communication
- TOPSIS-based inter-RSU load balancing
- Deterministic SIC enforcement
- PER-aware optimization

The framework jointly optimizes:

- Age of Information (AoI)
- Energy Consumption
- Rental Cost
- Packet Error Rate (PER)

Experiments were conducted under both normal and congested traffic scenarios using two different map settings.

---

# Authors

- Himanshi (2022UCA1802)
- Tripti Gusain (2022UCA1812)
- Varu Solanki (2022UCA1873)

Department of Computer Science and Engineering  
Netaji Subhas University of Technology (NSUT), New Delhi

---

# Repository Structure

```plaintext
NOMA-TD3-TOPSIS/
│
├── README.md
│
├── notebooks/
│   ├── main_experiments.ipynb
│   └── paper_plots.ipynb
│
├── RESULTS/
│   ├── MAP1
│   └── MAP2
│
├── PLOTS/
│   ├── MAP1
│   └── MAP2
````

---

# Open in Google Colab

* Main Experiments Notebook: [Add Colab Link Here]
* Plot Generation Notebook: [Add Colab Link Here]

---

# How to Run the Experiments

A total of 8 experiment combinations were evaluated, varying the map, traffic scenario, and the use of NOMA and TOPSIS.

The same notebook (`main_experiments.ipynb`) is used for all experiments. You simply need to change the configuration flags for each run.

---

## 1. Setup the Environment

Open `notebooks/main_experiments.ipynb` in Google Colab.

Enable GPU runtime:

```plaintext
Runtime → Change Runtime Type → Select GPU
```

---

## 2. Configure Your Experiment

At the top of the notebook, you will find a configuration block.

To run a specific experiment, update the variables:

* `EXPERIMENT_NAME`
* `NOMA_ENABLED`
* `TOPSIS_ENABLED`
* `scenario`
* `map_name`

according to the tables below.

---

## Case 1: Map 1 (Normal Traffic Scenario)

| Experiment Name      | NOMA_ENABLED | TOPSIS_ENABLED | scenario   | map_name |
| -------------------- | ------------ | -------------- | ---------- | -------- |
| NOMA_TD3_TOPSIS | True         | True           | `'normal'` | `'map1'` |
| NOMA_TD3        | True         | False          | `'normal'` | `'map1'` |
| TD3_TOPSIS      | False        | True           | `'normal'` | `'map1'` |
| TD3             | False        | False          | `'normal'` | `'map1'` |

---

## Case 2: Map 2 (Congested Traffic Scenario)

| Experiment Name      | NOMA_ENABLED | TOPSIS_ENABLED | scenario      | map_name |
| -------------------- | ------------ | -------------- | ------------- | -------- |
| NOMA_TD3_TOPSIS | True         | True           | `'congested'` | `'map2'` |
| NOMA_TD3        | True         | False          | `'congested'` | `'map2'` |
| TD3_TOPSIS      | False        | True           | `'congested'` | `'map2'` |
| TD3             | False        | False          | `'congested'` | `'map2'` |

---

## Example Configuration (NOMA_TD3)

```python
EXPERIMENT_NAME = 'NOMA_TD3'

NOMA_ENABLED = True
TOPSIS_ENABLED = False

scenario = 'congested'
map_name = 'map2'
```

---

## 3. Run the Code

Once you have entered the correct flags for your desired experiment, run all cells:

```plaintext
Runtime → Run all
```

> **Note:** You will need to repeat this process for each of the 8 configurations to generate all necessary results.

---

# Plot Generation

Update the map_name
To generate publication-quality plots used in the report:

1. Ensure you have already run the required experiments so that the results data is saved.
2. Open `notebooks/paper_plots.ipynb` in Google Colab.
3. In Cell 2, configure the 4 Google Drive paths to point to your saved:

   * `training_metrics.json`
   * `evaluation_results.json`
4. In Cell2 only, be sure to set the correct `map_name` (either `MAP1` or `MAP2`) depending on which scenario’s results you want to plot.

   Example:

   ```python
   map_name = "MAP1"
   ```
5. Run all cells.

All plots will automatically be saved as high-resolution PNG files to your Google Drive.

---

# Result Storage Paths

All experiment outputs are automatically saved to Google Drive.

Base result directory:

```plaintext
/content/drive/MyDrive/RESULT/
```

The final two folders depend on the selected map and experiment configuration.

Example:

```plaintext
/content/drive/MyDrive/RESULT/MAP1/NOMA_TD3
```

Thus, the structure follows:

```plaintext
/content/drive/MyDrive/RESULT/<MAP_NAME>/<EXPERIMENT_NAME>
```

---

# Plot Storage Paths

After running `paper_plots.ipynb`, all generated plots are saved automatically to:

```plaintext
/content/drive/MyDrive/PLOTS/
```

The same map-wise structure is followed.

Example:

```plaintext
/content/drive/MyDrive/PLOTS/MAP1/NOMA_TD3
```

General structure:

```plaintext
/content/drive/MyDrive/PLOTS/<MAP_NAME>/<EXPERIMENT_NAME>
```


# Notes

* The implementation was developed and tested using Google Colab
* Ensure your Google Drive is properly mounted when prompted.
* Models and metrics are saved directly to the Drive path specified in the notebooks.
```
```