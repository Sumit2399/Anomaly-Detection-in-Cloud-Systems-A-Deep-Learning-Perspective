# 🚀 Cloud Anomaly Detection on IBM Cloud Console Telemetry

This project applies **six deep learning architectures** to detect anomalies in real IBM Cloud Console telemetry.
The goal is to evaluate how different model families (GRU, Transformer, TimesNet, Autoformer, and Anomaly Transformer) behave on *noisy, irregular, real-world cloud data* where anomalies are short-lived and context-dependent.

The models predict or reconstruct normal system behavior, and deviations are scored using the **NAB (Numenta Anomaly Benchmark)** — a timing-aware metric suited for cloud systems.


# 📥 Download the Dataset

The full dataset used in this project (pivoted telemetry + anomaly windows) is publicly available on Zenodo:

🔗 **Download Link:**
[https://zenodo.org/records/14062900](https://zenodo.org/records/14062900)

Download the ZIP file, extract it, and you will find:

```
pivoted_data.parquet
anomaly_windows.csv
```


# 📁 Setup Instructions

### 1️⃣ Place data files in your working directory

After downloading, move both files into a folder of your choice, for example:

```
data/
   pivoted_data.parquet
   anomaly_windows.csv
```

### 2️⃣ Open any notebook in `scripts/`

Inside the repository, all model implementations are in:

```
scripts/
   GRU_Baseline.ipynb
   GRU_Improved.ipynb
   Transformer_Baseline.ipynb
   AnomalyTransformer.ipynb
   TimesNet.ipynb
   Autoformer.ipynb
```

### 3️⃣ **Update the file paths at the top of each notebook**

Every notebook contains variables at the top, such as:

```python
PIVOTED_FILE = "path/to/pivoted_data.parquet"
ANOMALY_WINDOWS_FILE = "path/to/anomaly_windows.csv"
```

👉 **Change these to the exact path where you saved the downloaded files.**
Example:

```python
PIVOTED_FILE = "data/pivoted_data.parquet"
ANOMALY_WINDOWS_FILE = "data/anomaly_windows.csv"
```


# ▶️ Running the Notebooks

Once the file paths are updated:

1. Open the notebook you want to run
2. Run all cells from top to bottom
3. The notebook will automatically:

   * load the dataset
   * train the model
   * compute MSE/discrepancy scores
   * generate anomaly likelihood curves
   * evaluate using the NAB score
   * export CSVs + visualizations to `userData/`

There is **no need to modify any other code** unless you want to tune parameters.


# 🧠 Models Included (6 Total)

This project implements and benchmarks the following:

* **GRU Baseline Autoencoder**
* **Improved GRU (MAD + shaped alerts)**
* **Transformer Autoencoder**
* **Anomaly Transformer**
* **TimesNet**
* **Autoformer**

Each notebook is self-contained and can be run independently.


# 📝 Summary

This repository provides a full pipeline for evaluating modern anomaly detection architectures on real cloud telemetry.
It serves as both:

✔ a research benchmark comparison
✔ a practical anomaly detection prototype for cloud operations


