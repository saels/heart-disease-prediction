# ❤️ Heart Disease Modeling: Clinical Features vs. ECG Signals

## 💼 Business use case

These two projects address cardiovascular screening from very different data sources. The **clinical heart-disease model** uses structured clinical variables to estimate a binary disease target, which fits a patient-level triage or retrospective risk-analysis workflow. The **ECG5000 model** classifies individual waveform traces as normal or abnormal, which is closer to automated signal screening and review prioritization.

The models therefore complement each other rather than compete directly: one reasons from patient attributes, while the other learns from the morphology of a physiological signal.

## 🎯 Principal objective

The **tabular neural-network notebook** combines numerical and categorical clinical features, applies leakage-safe preprocessing, preserves class balance with a stratified split, and trains a binary neural-network classifier.

The **ECG5000 notebook** works with 140-point ECG traces, normalizes the signal features, and trains a compact feed-forward network to separate normal from abnormal waveforms. It also benchmarks the model against the majority class.

## 🔎 Summary of takeaways

The tabular model reaches **80.33% test accuracy**, above its roughly **72.61% majority-class baseline**. The result shows useful predictive signal in the clinical features, but a serious medical review would still require sensitivity, specificity, ROC-AUC, calibration, subgroup analysis, and clinically meaningful threshold selection.

The ECG model reaches **99.2% test accuracy** with test loss around **0.0336**, compared with a **58.4% majority-class baseline**. That benchmark result is substantially higher, but it comes from a different dataset and prediction problem, so the two accuracy values should not be treated as a head-to-head model comparison. The ECG project would benefit from abnormal-class sensitivity, patient-level splitting, rhythm-subtype analysis, and comparison with architectures such as 1D CNNs that explicitly model local temporal structure.

Together, the notebooks demonstrate how the representation of medical data changes the engineering problem: clinical models depend heavily on preprocessing and feature semantics, while waveform models must preserve and learn structure across a sequence.

## 🧭 Explore the code

Open both notebooks to compare the pipelines directly. The [clinical heart-disease project](https://github.com/saels/heart-disease-prediction/blob/c703ef8fde09e22044307a2c7046163d67dd17ab/Heart_Disease_Neural_Network.ipynb) highlights structured preprocessing and patient-level classification; the [ECG project](https://github.com/saels/heart-disease-prediction/blob/52adece25538aa4118566d5539d816cef9d6de3f/ECG5000_Abnormality_Classifier.ipynb) shows how a fixed-length signal can be normalized and fed into a neural network. Reviewing the code side by side gives a useful view of how model design changes with the data modality.
