# Pricing_ML

**Pricing_ML** builds on the existing [Pricing repository](https://github.com/rimchmielowitz/Pricing) and extends its logic with **Machine Learning** components. The base concept remains the same: customer tasks (orders) are matched with potential drivers (ODs), and a dynamic pricing mechanism determines individual prices based on **Willingness to Pay (WTP)** and **Expectation to be Paid (ETP)**.

---

## 🔗 Mathematical Model Reference

The mathematical formulation of the pricing model — including all constraints, objectives, and variables — is fully documented in the original [Pricing repository](https://github.com/rimchmielowitz/Pricing).  
This repository focuses **only** on the **integration of ML** to replace the stochastic elements (random WTP/ETP values) with **data-driven predictions**.

---

## 📦 What's Inside

- `Pricing_ML.ipynb`: Main notebook (Google Colab compatible), which includes:
  - ML-based estimation of WTP and ETP using **Bayesian Regression** (via [Pyro](https://pypi.org/project/pyro-ppl/))
  - Integration of predicted WTP/ETP values into a **Mixed Integer Programming** model using [OR-Tools](https://developers.google.com/optimization)
  - Visualization & analysis of results (e.g., routes, Gantt charts, distance comparisons)

- Supporting functions for:
  - Instance loading and preparation
  - ML model training
  - Optimization model setup and solving
  - Result aggregation and plotting

---

## 🚀 How to Use

[👉 Open in Google Colab](https://colab.research.google.com/github/rimchmielowitz/Pricing_ML/blob/main/Pricing_ML.ipynb)

Simply run the notebook.  
All required packages will be installed automatically, and example data is already included. No manual setup or data upload needed.

---

## 📊 ML vs. Randomized Approach

To demonstrate the real-world impact of using ML-predicted values instead of random sampling, we compare two optimization runs with:

- **8 tasks**
- **10 available drivers**

### Results Summary

| Method             | Total Distance (km) | Saved Distance (km) | Relative Reduction |
|--------------------|---------------------|----------------------|--------------------|
| Randomized WTP/ETP | 36.26               | –                    | –                  |
| ML-based WTP/ETP   | 31.40               | **4.86**             | **≈13.4 %**        |

> In this case, the ML-based method reduces the total distance traveled by nearly 13.4%, while maintaining full task fulfillment.

---

### 📈 Gantt Chart Comparison

**Without ML:**

![Gantt without ML](https://github.com/user-attachments/assets/074d5b19-b6f0-499d-8e73-5e88eed2bb0d)


**With ML:**

![Gantt with ML](https://github.com/user-attachments/assets/ca92c875-e3c5-48bc-858b-10a7091ccbbb)

---

### 🗺️ Route Map Comparison

**Without ML:**

![Map without ML](https://github.com/user-attachments/assets/9f46aa41-4296-4479-911e-a137ceae2d5a)


**With ML:**

![Map with ML](https://github.com/user-attachments/assets/86868f7c-1228-4f7b-a0a2-19f947aca3ea)


---

These visual and numerical results support the effectiveness of replacing randomly drawn WTP/ETP values with machine learning models trained on realistic inputs. The improvement in route efficiency is clear and reproducible across different scenarios.

The bar chart below compares total driving distances using the **ML-based method** vs. the **randomized method** across different SPL-DMD levels (driver-to-order ratios). Each scenario contains 10 orders.

![image](https://github.com/user-attachments/assets/56f8d9da-be96-4a7f-a53c-1052ace08ac7)


- **Gray area**: Total baseline distance (drivers traveling from their start to end node without fulfilling orders)
- **Orange area**: Additional detour distance with **randomized WTP/ETP**
- **Blue area**: Additional detour distance with **ML-predicted WTP/ETP**

> From a ratio of 1.2 drivers per task onward, detour distances are reduced by up to **35.76%** using the ML method compared to random values.

This demonstrates how machine learning can significantly improve efficiency and reduce unnecessary kilometers in task assignment.

---

## ✅ Summary

- **Improved efficiency** through smarter WTP and ETP predictions
- **Seamless integration** with the existing pricing logic and optimization model
- **No manual setup required** – just open the notebook and run

For the full mathematical formulation, please visit the [original Pricing repository](https://github.com/rimchmielowitz/Pricing).

---

## 📄 License & Contact

- **License**: [MIT License](LICENSE) 
- **Contact**: Questions or suggestions? Feel free to open an issue or reach out via [E-mail](mailto:rimchmielowitz@gmail.com)

---

**Have fun exploring, optimizing, and improving logistics with data!**
