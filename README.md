## Evaluating Overprecision in Black-Box LLMs
This repository contains a reproducible implementation of a cognitive-science-inspired framework to evaluate overprecision in black-box large language models (LLMs). The pipeline elicits numeric confidence intervals from LLMs at imposed confidence levels, applies optional refinement (aggregation and self-refinement), and evaluates calibration and responsiveness with dedicated metrics.
> Overprecision: unwarranted certainty reflected in intervals that are too narrow for the stated confidence (e.g., a “90% interval” that covers far less than 90% of truths). The framework uses three phases—Generation → Refinement → Evaluation—mirroring Figure 1 in the paper (prompting & sampling; aggregation or self-refinement; calibration metrics).

### Repository structure
All code is provided as Jupyter notebooks so you can run the full workflow interactively:
- `Overconfidence_Clean_Output_Format.ipynb` — helpers to standardize model outputs for downstream evaluation. 
- `Overconfidence_Measures_and_Aggregation_(Width_and_Deviation).ipynb` — computes metrics (hit@c, correlation, Deviation Score, Interval Length Score) and implements aggregation strategies (Mean, Length-Weighted, Inverse-Length-Weighted, Union, Confidence-Weighted). 
- `Overconfidence_Measures_and_Aggregation_Test_2.ipynb / _Test_3.ipynb` — additional metric/aggregation experiments.
- `Overconfidence_Overprecision_Inference_Parallel_1.ipynb / _2.ipynb` — Generation phase: prompt LLMs to produce numeric intervals under imposed confidence levels (60/70/80/90/95), with multiple samples per question. 
- `Overconfidence_Self_Refine_Overprecision_Inference_Parallel_1.ipynb` — Self-refinement: the model reviews candidate intervals and optionally proposes a new one. 
- `Overconfidence_Self_Refine_Overprecision_Interval_Analysis.ipynb` — analyzes self-refinement behaviors (e.g., tendency to favor the narrowest intervals).

### Method overview (what the notebooks implement)
1- Generation:
  - Prompting strategies:
    - Vanilla: directly ask for lower/upper bounds at confidence level c.
    - CoT: same, with step-by-step reasoning requested.
  - Sampling strategy: multiple runs per question to capture stochasticity (“self-random”).
