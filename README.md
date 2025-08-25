Energy Churn and Pricing-Impact Analysis
This project analyzes customer churn in energy retail and quantifies how lifecycle, product mix, consumption, and tariff prices relate to churn and profitability to inform targeted retention near renewal. It joins a customer-level table (consumption, margins, product counts, power, lifecycle dates, churn) with a monthly tariff price series (off/mid/peak, fixed/variable) keyed by id and price_date, producing a merged, model-ready view for diagnostics.

Objectives
Predict which customers are most likely to churn around renewal windows and explain the drivers using lifecycle and pricing features.

Measure the relationship between recent price levels and churn risk to inform timing and messaging of price changes.

Translate insights into retention actions prioritized by expected economic value (net margin preserved vs. incentive/outreach cost).

What’s in this repo
Notebook: bcg_churn_pricing_analysis.ipynb (name suggestion) containing:

Project overview (objective, data sources, prediction time, target, success metrics).

Feature list (name, definition, window, leakage notes) matching existing fields, no code changes required.

Business recommendations (ROI‑based retention, price‑change communication triggers, proactive outreach near T−30 days for high pow_max segments).

EDA/modeling sections that operate on the customers table, prices table, and a joined month-level price view.

Optional: README.md (this file), requirements.txt, and a lightweight data dictionary if sharing schemas.

Data overview
Customers table (columns include): id, channel_sales, cons_12m, cons_last_month, cons_gas_12m, date_activ, date_modif_prod, date_renewal, date_end, margin_gross_pow_ele, margin_net_pow_ele, net_margin, nb_prod_act, has_gas, pow_max, origin_up, num_years_antig, churn.

Prices table: id, price_date, price_off_peak_var, price_peak_var, price_mid_peak_var, price_off_peak_fix, price_peak_fix, price_mid_peak_fix.

Merged view: customers joined to monthly prices by id and price_date for lifecycle- and price-aware analysis and modeling.

Feature documentation (matches notebook)
Consumption: cons_12m, cons_last_month, cons_gas_12m.

Margins and economics: margin_gross_pow_ele, margin_net_pow_ele, net_margin.

Lifecycle and product mix: date_activ/date_modif_prod/date_renewal/date_end, nb_prod_act, has_gas, pow_max, num_years_antig.

Segmentation: channel_sales, origin_up.

Pricing (monthly): off/mid/peak, fixed/variable prices keyed by price_date.

How to use
Open the notebook in JupyterLab or GitHub’s viewer to read the overview, feature list, and recommendations before diving into analysis cells.

If executing locally, install dependencies and ensure customer and price tables are available in the expected structure (paths may be environment-specific).

Environment
Python 3.x with typical data stack (pandas, numpy; modeling libraries if included in the notebook). A minimal requirements.txt is recommended if running the notebook end‑to‑end.

Business recommendations (from the notebook)
Targeted retention by ROI: Prioritize customers with higher net margins and approaching renewal when churn risk and expected value justify intervention; cap outreach to reduce fatigue.

Price-change communication: If recent price levels (e.g., off-peak variable or peak fixed) increased in the months before renewal, use proactive messaging and plan options to mitigate churn.

Proactive renewal outreach: For high pow_max segments, stage offers from advice to conditional credits only if risk remains elevated after initial contact.

