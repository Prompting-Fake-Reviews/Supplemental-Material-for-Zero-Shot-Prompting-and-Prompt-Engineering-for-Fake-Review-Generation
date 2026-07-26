# AI-Generated Fake Review Dataset

This repository contains AI-generated fake reviews generated as part of the study:

**Prompting Credibility: Risks of Zero-Shot Prompting and Prompt Engineering for Fake Review Generation**

The study investigates whether **zero-shot prompt engineering** can be used to generate fake online reviews that mimic genuine review characteristics. Guided by **Information Manipulation Theory (IMT)**, the experiments systematically manipulate textual, readability, sentiment, and temporal prompt constraints to evaluate the similarity between AI-generated fake reviews and genuine Yelp reviews, as well as the impact on fake review detection.

The repository currently provides the **GPT-generated fake reviews** (GPT-4.1) together with all automatically extracted review metrics used throughout the experiments.


---

# Dataset Description

Each CSV file contains the generated review together with the linguistic and readability metrics calculated during the experiments.

Typical variables include:

| Variable | Description |
|----------|-------------|
| rating | Target star rating (1–5) |
| review | GPT-generated review |
| num_char | Number of characters |
| num_words | Number of words |
| num_sentences | Number of sentences |
| avg_sentence_length | Average sentence length |
| syllables | Number of syllables |
| FKGL | Flesch–Kincaid Grade Level |
| FRES | Flesch Reading Ease Score |
| FOG | Gunning Fog Index |
| CLI | Coleman–Liau Index |
| ARI | Automated Readability Index |
| DCRS | Dale–Chall Readability Score |
| polarity | Sentiment polarity |
| subjectivity | Subjectivity score |
| positive | Positive sentiment |
| neutral | Neutral sentiment |
| negative | Negative sentiment |
| prediction_lr | Logistic Regression prediction |
| prediction_xgb | XGBoost prediction |
| prediction_roberta | RoBERTa prediction |

---

# Experimental Design

The study comprises **19 prompt engineering experiments**, **356 experimental iterations**, and approximately **225,500 AI-generated fake reviews**.

Due to the large number of experimental iterations and AI-generated fake reviews, this repository currently provides the generated reviews and accompanying documentation for the final **Combining Best Practices** experiment, Combining Best Practices.
This experiment combines the best-performing prompt engineering strategies identified throughout the preceding experiments and serves as the final evaluation reported in the manuscript.

The repository therefore provides the AI-generated fake reviews together with all calculated review metrics for each iteration of the **Combining Best Practices** experiment.

---

# Combining Best Practices Experiment

The final experiment consists of multiple prompt engineering iterations. Each iteration incrementally extends the prompt by incorporating additional best-performing prompt components identified in previous experiments.
Per-rating parameterization
| Iteration | Prompt modification | Example prompt (5-star review) |
|-----------|---------------------|--------------------------------|
| [`combined_prompt_00_gen_sampled.csv`](combined_prompt_00_gen_sampled.csv), [`combined_prompt_01_gen_sampled.csv`](combined_prompt_01_gen_sampled.csv)| Baseline prompt | *Write exactly 10 reviews of a 5-star experience.* |
| [`combined_prompt_02_gen_sampled.csv`](combined_prompt_02_gen_sampled.csv), [`combined_prompt_03_gen_sampled.csv`](combined_prompt_03_gen_sampled.csv) | Average number of sentences | *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length.* |
| [`combined_prompt_04_gen_sampled.csv`](combined_prompt_04_gen_sampled.csv), [`combined_prompt_05_gen_sampled.csv`](combined_prompt_05_gen_sampled.csv) | Average, range, and standard deviation of the number of sentences | *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. Reviews must vary in length by 4 sentences.* |
| [`combined_prompt_06_gen_sampled.csv`](combined_prompt_06_gen_sampled.csv), [`combined_prompt_07_gen_sampled.csv`](combined_prompt_07_gen_sampled.csv) | Sentence metrics and average Flesch–Kincaid Grade Level (FKGL) | *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. Reviews must vary in length by 4 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 5.7 on average.* |
| [`combined_prompt_08_gen_sampled.csv`](combined_prompt_08_gen_sampled.csv), [`combined_prompt_09_gen_sampled.csv`](combined_prompt_09_gen_sampled.csv) | Sentence metrics and two readability indices (FKGL and CLI), including means, ranges, and standard deviations| *Write exactly 10 reviews of a 4 star experience. Generate reviews that are on average 8 sentences in length and range from 1 to 28 sentences. Reviews must vary in length by 5 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 6.3 on average and a Coleman-Liau Index of 7.1 on average. They must range from 0.5 to 10.9 and vary by 1.84 for the Flesch-Kincaid Grade Level. They must range from 1.48 to 13.21 and vary by 1.88 for the Coleman-Liau Index.* |
| [`combined_prompt_10_gen_sampled.csv`](combined_prompt_10_gen_sampled.csv), [`combined_prompt_11_gen_sampled.csv`](combined_prompt_11_gen_sampled.csv) | Sentence metrics (without standard deviation) and FKGL, including mean, range, and standard deviation| *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 5.7 on average. They must range from 1.9 to 21.2 and vary by 2.47 for the Flesch-Kincaid Grade Level.* |
| [`combined_prompt_12_gen_sampled.csv`](combined_prompt_12_gen_sampled.csv), [`combined_prompt_13_gen_sampled.csv`](combined_prompt_13_gen_sampled.csv) | Sentence metrics and FKGL constraints plus average neutral sentiment | *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 5.7 on average. They must range from 1.9 to 21.2 and vary by 2.47 for the Flesch-Kincaid Grade Level. Neutral sentiment can range from 0 to 1. The reviews must match a neutral sentiment of 0.7 on average.*|
| [`combined_prompt_14_gen_sampled.csv`](combined_prompt_14_gen_sampled.csv), [`combined_prompt_14_gen_sampled.csv`](combined_prompt_14_gen_sampled.csv) | Sentence and FKGL constraints plus neutral-sentiment mean, range, and standard deviation | *Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 5.7 on average. They must range from 1.9 to 21.2 and vary by 2.47 for the Flesch-Kincaid Grade Level. Neutral sentiment can range from 0 to 1. The reviews must match a neutral sentiment of 0.7 on average.The reviews must vary in neutral sentiment by 0.12 and range from a neutral sentiment of 0.24 to 0.93.* |
| [`combined_prompt_16_gen_sampled.csv`](combined_prompt_16_gen_sampled.csv), [`combined_prompt_17_gen_sampled.csv`](combined_prompt_17_gen_sampled.csv) | Sentence, readability, and sentiment constraints, plus subjectivity mean, range, and standard deviation |*Write exactly 10 reviews of a 5 star experience. Generate reviews that are on average 7 sentences in length and range from 1 to 22 sentences. Reviews must vary in length by 4 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 5.7 on average. They must range from 1.9 to 21.2 and vary by 2.47 for the Flesch-Kincaid Grade Level. Neutral sentiment can range from 0 to 1. The reviews must match a neutral sentiment of 0.7 on average.The reviews must vary in neutral sentiment by 0.12 and range from a neutral sentiment of 0.24 to 0.93. Subjectivity can range from 0 to 1. The reviews must match a mean subjectivity of 0.6.The reviews must vary in subjectivity by 0.12 and range from a subjectivity of 0.0 to 0.88.*|
| [`combined_prompt_18_gen_sampled.csv`](combined_prompt_18_gen_sampled.csv), [`combined_prompt_19_gen_sampled.csv`](combined_prompt_19_gen_sampled.csv) | Sentence, readability, sentiment, and subjectivity constraints plus temporal prompting (publication year 2012) | *Write exactly 10 reviews of a 4 star experience. Generate reviews that are on average 8 sentences in length and range from 1 to 28 sentences. Reviews must vary in length by 5 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 6.3 on average. They must range from 0.5 to 10.9 and vary by 1.84 for the Flesch-Kincaid Grade Level. Neutral sentiment can range from 0 to 1. The reviews must match a neutral sentiment of 0.74 on average.The reviews must vary in neutral sentiment by 0.09 and range from a neutral sentiment of 0.35 to 0.92. Subjectivity can range from 0 to 1. The reviews must match a mean subjectivity of 0.58.The reviews must vary in subjectivity by 0.12 and range from a subjectivity of 0.0 to 0.92. Write the review exactly like it was written in 2012.* |
| [`combined_prompt_20_gen_sampled.csv`](combined_prompt_20_gen_sampled.csv), [`combined_prompt_21_gen_sampled.csv`](combined_prompt_21_gen_sampled.csv)| Sentence, readability, sentiment, and subjectivity constraints plus temporal prompting (publication year 2018) | *Write exactly 10 reviews of a 1 star experience. Generate reviews that are on average 9 sentences in length and range from 1 to 23 sentences. Reviews must vary in length by 5 sentences. The generated reviews must have a Flesch-Kincaid Grade Level of 6.1 on average. They must range from 2.1 to 15.0 and vary by 2.21 for the Flesch-Kincaid Grade Level. Neutral sentiment can range from 0 to 1. The reviews must match a neutral sentiment of 0.79 on average. The reviews must vary in neutral sentiment by 0.09 and range from a neutral sentiment of 0.54 to 1.0. Subjectivity can range from 0 to 1. The reviews must match a mean subjectivity of 0.54. The reviews must vary in subjectivity by 0.14 and range from a subjectivity of 0.12 to 1.0. Write the review exactly like it was written in 2018.* |
| combine_22-43 | Same as in Iteration 0-21 | Iterations 22–43 tested the same combinations as Iterations 0–21, but with Meta-Prompting (ses table below), requesting a rewrite of the prompts for star ratings from 1 to 5 to achieve optimal results. |

---
# Meta-Prompting 
The table below show the system prompt for Iteration 42 and Iteration 43, which combine all best practices with Meta-Prompting for generating 5-star reviews. 

| System Prompt | Iteration(s) | Example User Prompt (5-Star Reviews) |
|---|---|---|
| *You are simulating a restaurant customer writing detailed reviews. Your tone should match an enthusiastic, delighted, and highly satisfied experience. All responses should reflect the style of reviews written in 2018.* | [`combined_prompt_42_gen_sampled.csv`](combined_prompt_42_gen_sampled.csv), [`combined_prompt_43_gen_sampled.csv`](combined_prompt_43_gen_sampled.csv) | Write exactly 10 unique restaurant reviews based on a 5-star experience. Use a tone and language style consistent with 2018 online reviews.<br><br>Guidelines:<br>-Sentence Count:<br>&nbsp;&nbsp;&nbsp;&nbsp;- Average: 6.85 sentences<br>&nbsp;&nbsp;&nbsp;&nbsp;- Range: 1 to 22 sentences<br>&nbsp;&nbsp;&nbsp;&nbsp;- Must vary by at least 4.27 sentences between reviews<br>-Flesch–Kincaid Grade Level:<br>&nbsp;&nbsp;&nbsp;&nbsp; - Average: 5.66<br>&nbsp;&nbsp;&nbsp;&nbsp; - Range: 1.90–21.20<br>&nbsp;&nbsp;&nbsp;&nbsp; - Must vary by at least 2.47 points<br>-Neutral Sentiment:<br>&nbsp;&nbsp;&nbsp;&nbsp; - Mean: 0.7<br>&nbsp;&nbsp;&nbsp;&nbsp; - Range: 0.24 to 0.93<br>&nbsp;&nbsp;&nbsp;&nbsp; - Must vary by at least 0.12<br>-Subjectivity:<br>&nbsp;&nbsp;&nbsp;&nbsp;- Mean: 0.6<br>&nbsp;&nbsp;&nbsp;&nbsp;- Range: 0.00 to 0.88<br>&nbsp;&nbsp;&nbsp;&nbsp;- Must vary by at least 0.12<br><br>Ensure all reviews sound natural, match the specified tone, and align with user-written content from the specified period. |



---
