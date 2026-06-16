# MOOC-Radar Student Behavior Clustering

This repository is dedicated to analyzing and clustering student learning behaviors within Massive Open Online Courses (MOOCs) using the **MOOC-Radar** dataset. By tracking student interaction patterns, course jumping sequences, and performance, this project aims to profile students into different learning styles (such as gamification user types).

---

##  Getting Started & Dataset Setup

To run the notebooks in this repository, you must first set up the dataset. 

1. **Download the Dataset:**
   Download the official MOOC-Radar dataset files from the following link:
    [Download MOOC-Radar Dataset](https://bhpan.buaa.edu.cn/anyshare/en-us/link/AAE5A458AFE444474EBEC928F98986E5B8/B787D29998CC4828AD4BD7AEEDB4AE45/667E34F342194C7EABBE0A94A32F134F/275D4A8183294772942B14554F49B66E?_tb=none)

2. **Place Files in the Repository:**
   Extract and place the downloaded JSON files inside a `datasets` folder at the root of this project:
   ```bash
   datasets/
   ├── problem.json
   ├── student-problem-coarse.json
   ├── student-problem-fine.json
   └── student-problem-middle.json
   ```

---

##  Project Workflow

The analysis and modeling pipeline is divided across the following Jupyter notebooks:

1. **`EDA.ipynb`**
   * Performs exploratory data analysis on the raw datasets.
   * Examines shapes, types, problem attributes, and basic statistics of student interactions.

2. **`pre_clustering.ipynb`**
   * Handles multi-granularity loading (fine, coarse, and middle levels) of student problem interaction logs.

3. **`clustering.ipynb`** (Main Pipeline)
   * **Preprocessing:** Merges flattened student logs with problem metadata and sorts interactions chronologically.
   * **Feature Engineering:** Extracts 7 student-centric behavioral metrics:
     * *Temporal:* `median_time_between_attempts`, `active_days_count`.
     * *Effort & Tenacity:* `avg_attempts_per_problem`, `abandonment_rate`.
     * *Cognitive Strategy:* `avg_cognitive_dimension` (Bloom's dimension levels), `score_maximization_ratio`.
     * *Exploration:* `course_jumping_index` (rate of transitions between exercises).
   * **Preprocessing for Clustering:** Features are log-transformed (for skewed features like time gaps) and normalized using `StandardScaler`.
   * **Clustering Analysis:** Compares and applies clustering algorithms (like K-Means and DBSCAN) validated via the Elbow Method, Silhouette Score, and 2D/3D PCA visualization.

---

##  Prerequisites & Installation

To run the environment, install the standard Python data science libraries:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn
```
