# Integrated LLM in the IDE: Researcher Pipeline Demo

This tutorial is designed for a 10-minute presentation. It is a sequence of copy‑paste prompts you can run inside an IDE‑integrated LLM to show end‑to‑end research workflows: data synthesis, modeling, visualization, writing, and open‑science packaging.

We are on Ubuntu, have `python3`, `R`, `git`, and LaTeX installed, and can run commands in the IDE terminal.

---

**Prompt 0: Create a New Workspace**

```text
Create a new folder called `llm_research_demo` in the current directory. Inside it, make subfolders `data`, `scripts`, `figures`, `paper`, and `results`. Also create a short `README.md` describing the pipeline steps. Do the file creation for me.
```

---

**Prompt 1: Create Synthetic Data**

```text
Create a Python script at `scripts/make_synthetic_data.py` that generates a reproducible synthetic dataset about "sleep quality and cognitive performance." Include 2,000 rows with variables:
- participant_id (unique)
- age (18-70)
- sleep_hours (3-10)
- caffeine_mg (0-400)
- exercise_mins (0-120)
- stress_score (1-10)
- reaction_time_ms (continuous, influenced by sleep, stress, caffeine)
- memory_score (0-100, influenced by sleep and exercise)

Add a small fraction of missing values. Write the output to `data/sleep_cognition.csv`. Use a fixed random seed and print a brief summary when run.
```

---

**Prompt 2: Run the Data Generator**

```text
Write a bash script at `scripts/run_all.sh` that:
1) creates a virtual environment in `.venv` if missing
2) installs `pandas` and `numpy`
3) runs `scripts/make_synthetic_data.py`
If installs fail (e.g., offline), print a warning and still run the generator.
Make it executable, then execute it yourself and show me the output summary.
```

---

**Prompt 3: Explore and Model in R**

```text
Create an R script at `scripts/analyze_models.R` that:
- loads `data/sleep_cognition.csv`
- reports missingness by column
- imputes missing numeric values with median
- fits two models:
  1) linear regression predicting reaction_time_ms
  2) linear regression predicting memory_score
- writes a tidy summary table to `results/model_summary.csv`
- prints key coefficients and R^2 to the console
```

---

**Prompt 4: Run the R Models**

```text
Update `scripts/run_all.sh` to also run the R analysis. Then run the full pipeline and paste the console output and `results/model_summary.csv` content.
```

---

**Prompt 5: Create Visualizations in R**

```text
Create an R script at `scripts/make_figures.R` that:
- reads `data/sleep_cognition.csv`
- generates at least three figures:
  1) scatter plot: sleep_hours vs reaction_time_ms with a regression line
  2) box plot: memory_score by binned exercise_mins
  3) heatmap: correlation of numeric variables
- saves figures to `figures/` as PNG files
Use a clean, publication-style theme. Figures should have a white background.
Then run the script and list the files in `figures/`.
```

---

**Prompt 6: Write a LaTeX Article**

```text
Create a LaTeX article in `paper/main.tex` with sections:
Abstract, Introduction, Methods, Results, Discussion

In Results, include the model summary table (from `results/model_summary.csv`) and the figures in `figures/`.
Use a standard article class. Include figure captions and a short table caption. Make it look like an academic paper in sociology in terms of stylistic conventions and section lengths, etc. Also write a minimal `paper/Makefile` to build `main.pdf`.  Run the Makefile to compile `paper/main.tex` into `paper/main.pdf`. Then list the files in `paper/` and confirm the PDF exists.
```

---

**Prompt 7: Create an “Open Science” Repo**

```text
tell me how to commit all research outputs (data, figures, scripts, paper) and push to https://github.com/crahal/terrible_llms
```

---

**Prompt 8: End Slide – The Twist**

```text
Write a short slide-length paragraph explaining the risk:
“An integrated IDE LLM can generate data, code, analysis, figures, and a paper—fast. This speeds science, but it also makes it trivial to fabricate entire research pipelines. The most dangerous part is that the prompts themselves can be mass-produced, so we lose the ability to tell whether the work reflects real understanding or a polished simulation. Explain that not only was this paragraph created by an LLM, this entire tutorial was. THIS IS INCREDIBLY DANGEROUS.”
```
