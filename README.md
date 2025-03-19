# Name-Gender-Bias Benchmark for Language Models
[Project Report](NGB_Benchmark_Report.pdf)

## Overview

The Name-Gender-Bias (NGB) Benchmark is designed to measure name association bias in language models. This benchmark evaluates whether language models assign pronouns (he/him, she/her, they/them) based on biased context when presented with names. The project leverages baby names data from the United States Social Security Administration and categorizes names into unisex and gender-specific groups for fine-grained analysis.

## Motivation

In natural language processing (NLP), mitigating bias is essential for creating fair and accurate language models. 

Our benchmark aims to:
- Evaluate how models respond to biased contexts when assigning pronouns.
- Provide a framework to compare models on their gender association tendencies.
- Identify potential areas of improvement in mitigating unintended gender bias.

## Dataset

The dataset is built using baby names from the US SSA since 1900 and consists of 1,000 samples divided into:
- **Unisex Names (700 samples):** Names with less than 85% usage for one gender are treated as unisex. These are further split into different thresholds to allow a detailed evaluation.
  - ![image](https://github.com/user-attachments/assets/4735b9e6-1b1e-4ce4-9e58-f926b020fbce)
- **Gender-Specific Names (300 samples):** This set includes popular and rare names that are predominantly used by one gender (e.g., 100 popular names per gender and 50 rare names per gender).

## Methodology

1. **Data Processing:**  
   - Combine annual baby names data into a unified dataset.
   - Calculate percentage scores for each name based on gender usage.
   - Categorize names into unisex and gender-specific groups using defined thresholds.

2. **Benchmark Construction:**  
   - **Prompts:** Each sample is paired with three prompts providing stereotypically male, female, or unbiased context.
   - **Task:** Models are tasked with selecting the appropriate pronoun (he/him, she/her, they/them) for each name based on the context.
   - **Evaluation:** The chosen pronouns are analyzed to determine whether the model’s assignment aligns with the inherent name usage statistics or is influenced by the provided biased context.

3. **Model Evaluation:**  
   The benchmark was used to assess several language models, including:
   - gemini-1.0-pro
   - gpt-3.5-turbo-0125
   - gpt-40-mini-2024-07-08
   - gpt-40-2024-08-06

## Results

Results indicate that while some models rely heavily on the provided context, others default to neutral choices (they/them), highlighting differences in bias handling.
![image](https://github.com/user-attachments/assets/6b703b65-a0cb-4e81-8f07-b7ba2f1ffae8)

- **Context Bias:**  
  Models such as gemini-1.0-pro and gpt-3.5-turbo-0125 tend to assign pronouns strongly influenced by the context, leading to disproportionate gender assignments for unisex names.

- **Model Comparison:**  
  Newer models (e.g., gpt-40-2024-08-06) often default to the safer, neutral option in ambiguous situations, suggesting improved bias mitigation.

- **Visual Analysis: How gpt-3.5-turbo-0125 model assigns pronouns based on different biased contexts**
  ![image](https://github.com/user-attachments/assets/23fc6cbe-eeab-4e39-a011-fe4a126b7f44)

  - The model tends to assign unisex names (names near x = 0) to the gender implied by the provided biased context.
  - Rare names sometimes receive pronouns opposite to the expected gender, likely due to similarities with female-associated names.
  - Some unisex names in neutral contexts are assigned nonneutral pronouns, suggesting possible bias in the training data or hidden biases within the model.

## Conclusion

Our NGB Benchmark provides a valuable framework for evaluating gender bias in language models. 

Key takeaways include:
- Even modern language models exhibit context-driven pronoun assignment biases.
- There is a notable difference in how models handle unisex versus gender-specific names.

Future work will focus on:
- Expanding the range of contexts and incorporating non-American names.
- Refining prompt designs to capture a broader spectrum of bias.
- Evaluating additional models to better understand bias trends and improvements over time.

## Authors

- Jonas Endriss
- Mohammad Zain Farooq Gill
- Yow Siao Kang
- Orgil Dorj
