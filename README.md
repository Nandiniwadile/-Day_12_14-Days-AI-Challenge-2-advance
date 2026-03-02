---

# 🚀 Day 12 – Cost Optimization Basics

📅 Date: 03/03/2026

## 🎯 Objective

The goal of Day 12 was to understand and apply basic cost optimization techniques in Spark and Databricks by:

* Analyzing job runtime
* Reducing unnecessary actions
* Documenting cost-saving ideas

Dataset used: `workspace.default.data`

---

# 📊 Step 1 – Load Dataset

The dataset was loaded from Unity Catalog to begin performance analysis.
This ensured correct catalog usage and avoided legacy Hive metastore errors.

---

# ⏱ Step 2 – Analyze Job Runtime (Baseline)

An aggregation was performed to count records by product.
This helped measure the initial execution time and observe shuffle behavior.

This step established the baseline runtime and cost.

---

# ⚠ Step 3 – Identify Unnecessary Actions

The same aggregation was executed multiple times.
This caused recomputation and triggered additional shuffle stages.

Observation:
Repeated actions increase cluster resource usage and execution cost.

---

# ✅ Step 4 – Apply Optimization

The aggregation result was stored in a variable and reused instead of recomputing it.
Filtering was applied on the precomputed result.

This reduced redundant execution and improved efficiency.

---

# 🔍 Step 5 – Execution Plan Analysis

The logical and physical execution plan was analyzed.

Key observations:

* Column pruning was applied (only required columns were scanned)
* Single aggregation stage executed
* Photon engine was used
* Query fully optimized by Spark

This confirmed efficient execution.

---

# 💰 Cost-Saving Learnings

1. Avoid repeated actions like multiple `.show()` calls.
2. Store intermediate results to prevent recomputation.
3. Understand Spark’s lazy evaluation model.
4. Minimize shuffle operations when possible.
5. Efficient transformations reduce compute cost more than just resizing clusters.

---

# 🏆 Final Outcome

✔ Job runtime analyzed
✔ Inefficient computations identified
✔ Optimized execution applied
✔ Execution plan verified
✔ Cost-saving strategies documented

---

# 🔥 Key Takeaway

Cost optimization in Spark is not only about cluster sizing —
it is about writing efficient transformations, reducing shuffles, and avoiding unnecessary actions.

---

