## Evaluating Overprecision in Black-Box LLMs
This repository contains a reproducible implementation of a cognitive-science-inspired framework to evaluate overprecision in black-box large language models (LLMs). The pipeline elicits numeric confidence intervals from LLMs at imposed confidence levels, applies optional refinement (aggregation and self-refinement), and evaluates calibration and responsiveness with dedicated metrics.
> Overprecision: unwarranted certainty reflected in intervals that are too narrow for the stated confidence (e.g., a “90% interval” that covers far less than 90% of truths). The framework uses three phases—Generation → Refinement → Evaluation—mirroring Figure 1 in the paper (prompting & sampling; aggregation or self-refinement; calibration metrics).
>
> 
