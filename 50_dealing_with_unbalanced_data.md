Here is a cheat sheet created from the provided transcript on dealing with unbalanced data:

---

**Cheat Sheet: Dealing with Unbalanced Data in Machine Learning**

- **Understanding Unbalanced Data:**
  - Occurs when there's a large discrepancy between classes (e.g., positive and negative cases) in training data.
  - Example domain: Fraud detection where fraudulent cases are much less frequent than non-fraudulent.

- **Impact on Models:**
  - Models may overpredict the majority class due to its prevalence in the training data, leading to misleading high accuracy.

- **Terminology Clarification:**
  - Positive Cases: Instances of the class we're interested in detecting (e.g., fraud in fraud detection, not necessarily 'good').
  - Negative Cases: Instances of the class that does not represent the event of interest (e.g., legitimate transactions in fraud detection).

- **Common Problem in:**
  - Neural networks and other algorithms that learn from data distribution.

- **Strategies for Handling Unbalanced Data:**

  1. **Oversampling:**
     - Duplicate samples from the minority class to balance the dataset.
     - Helps even though it seems counterintuitive as it can provide neural networks with more examples to learn from.

  2. **Undersampling:**
     - Remove samples from the majority class to balance the dataset.
     - Not generally recommended as it involves discarding data, which could be avoided by scaling up computational resources.

  3. **SMOTE (Synthetic Minority Oversampling Technique):**
     - Artificially generates new samples of the minority class using the K-Nearest Neighbors algorithm.
     - Creates synthetic, yet plausible, samples based on the mean of K-nearest neighbors, improving upon simple oversampling.

- **Adjusting Inference Thresholds:**
  - Modify the probability threshold for classification to manage false positives and negatives.
  - Increase threshold to reduce false positives (at the cost of increasing false negatives) and vice versa.
  - Balance the threshold based on the cost implications of false positives vs. false negatives.

**Key Considerations:**
- Understand the business impact of false positives and false negatives.
- Choose techniques based on the context and computational resources.
- Ensure techniques do not introduce bias or overfitting.

---

This cheat sheet encapsulates the main points from the transcript and is meant to be a quick reference for dealing with unbalanced datasets. Make sure you also understand the theory behind these techniques and are able to implement them using AWS tools like Amazon SageMaker.

Based on the provided transcript, here are several practice exam questions regarding unbalanced data and methods to address it in machine learning:

1. **Question**: In the context of machine learning, when discussing 'positive' and 'negative' cases in feature engineering, what does 'positive' actually refer to?
   
   - A) Morally good outcomes
   - B) The class of outcomes you're trying to detect
   - C) The majority class in the dataset
   - D) The class with more favorable outcomes

2. **Question**: Which of the following is NOT a good reason to choose under-sampling to deal with unbalanced datasets?
   
   - A) You want to avoid throwing away potentially valuable data.
   - B) You're trying to address a scaling issue with limited hardware.
   - C) You prefer to increase the number of minority class instances.
   - D) You wish to balance the dataset without fabricating data.

3. **Question**: What does SMOTE stand for in the context of handling unbalanced datasets?
   
   - A) Simple Minority Overweighting Technique
   - B) Synthetic Minority Oversampling Technique
   - C) Synthetic Majority Oversampling Technique
   - D) Simple Majority Overweighting Technique

4. **Question**: How does SMOTE generate new samples for the minority class?
   
   - A) By randomly cloning existing minority class samples.
   - B) By creating averages of the majority class samples.
   - C) By generating new samples based on nearest neighbors and taking the mean.
   - D) By oversampling the majority class to match the minority class.

5. **Question**: Adjusting the threshold for prediction probability can help balance the trade-off between false positives and false negatives. What is a possible consequence of increasing this threshold in a fraud detection model?
   
   - A) Increase in false positives
   - B) Increase in true negatives
   - C) Increase in false negatives
   - D) Decrease in overall accuracy

---

### Answers and Explanations:

1. **Answer**: B) The class of outcomes you're trying to detect
   - **Explanation**: 'Positive' in the context of machine learning classification refers to the class of outcomes that the model is attempting to detect, regardless of whether the outcome is good or bad from a moral or subjective standpoint.

2. **Answer**: C) You prefer to increase the number of minority class instances.
   - **Explanation**: Under-sampling involves removing instances from the majority class to balance the data, which is contrary to the aim of increasing the number of minority class instances. This can result in the loss of valuable data.

3. **Answer**: B) Synthetic Minority Oversampling Technique
   - **Explanation**: SMOTE stands for Synthetic Minority Oversampling Technique. It is a method used to create artificial data points for the minority class based on the existing data points, helping to balance the dataset.

4. **Answer**: C) By generating new samples based on nearest neighbors and taking the mean.
   - **Explanation**: SMOTE works by applying the K-nearest neighbors algorithm to the minority class instances and then creating synthetic instances by taking the mean of the neighbors, thereby generating new, non-replicated data points.

5. **Answer**: C) Increase in false negatives
   - **Explanation**: Increasing the threshold for predicting an event (like fraud) means that the model becomes more conservative, hence it predicts fewer positives and, as a consequence, may miss actual positive cases, leading to an increase in false negatives. This might be chosen to reduce the number of false positives, but at the cost of potentially overlooking true positive cases.
   