# DS 6050 Final Project

## Real-Time Traffic Sign Classification using CNNs

**Authors:** Shawn Kubo et al.

---

### Overview
This project implements and compares convolutional neural network (CNN) architectures for real-time classification of traffic signs using the [GTSRB (German Traffic Sign Recognition Benchmark)](https://benchmark.ini.rub.de/) dataset. The goal is to demonstrate that a custom CNN with dropout regularization and data augmentation can outperform the classic LeNet-5 baseline, especially in terms of generalization.

### Hypothesis
A custom CNN architecture with dropout regularization and data augmentation will outperform the historical LeNet-5 baseline. Dropout is expected to reduce the generalization gap between training and validation performance.

---

## Dataset
- **Source:** GTSRB (German Traffic Sign Recognition Benchmark)
- **Classes:** 43 traffic sign categories
- **Images:** ~50,000 real-world images
- **Splits:** Stratified 80/20 train/validation split, plus a held-out test set

---

## Project Structure
- `Final project.ipynb`: Main notebook with code, results, and analysis
- `primary_model.h5`: Saved Keras model weights for the best model
- `Meta.csv`, `Train.csv`, `Test.csv`: Metadata and data splits
- `data/`: Directory containing image data

---

## Approach
1. **Data Loading & Preprocessing**
   - Downloaded via `kagglehub`
   - Images resized to 32×32 px, normalized to [0, 1]
   - Data augmentation: random rotation (±15°) for training
2. **Exploratory Data Analysis (EDA)**
   - Visualized sample images and class distribution
3. **Model Architectures**
   - **LeNet-5 (Baseline):** Classic 1998 architecture
   - **Custom CNN (Primary):** Two convolutional blocks, dense head, dropout
   - **Custom CNN (Ablation):** Same as primary, but without dropout
4. **Training & Evaluation**
   - All models trained for 10 epochs
   - Early stopping and validation monitoring
   - Performance measured on held-out test set
5. **Analysis**
   - Learning curves, confusion matrix, per-class recall
   - Error analysis: misclassifications and confident failures
   - 5-fold cross-validation for robust accuracy estimates
   - Simulated real-time webcam demo

---

## Results
| Model                        | Test Accuracy |
|------------------------------|--------------|
| LeNet-5 (Baseline)           | ~88.8%       |
| Custom CNN — No Dropout      | ~92.1%       |
| Custom CNN + Dropout (Primary)| ~92.5%      |

- Custom CNN outperforms LeNet-5 by ~3–4 percentage points
- Dropout provides a modest but consistent improvement (~0.5%)
- Cross-validation confirms stability across splits
- Hardest classes share visual similarity, suggesting further improvements via targeted augmentation or class-weighted loss

---

## How to Run
1. Install dependencies (see notebook for full list):
   - TensorFlow, Keras, pandas, numpy, matplotlib, seaborn, scikit-learn, PIL, kagglehub
2. Download the GTSRB dataset using the notebook code
3. Run `Final project.ipynb` cell by cell
4. (Optional) Use the provided model weights for inference

---

## Future Work
- Batch normalization
- Deeper architectures (e.g., ResNet-style skip connections)
- Class-balanced sampling
- Deployment with a live webcam inference loop

---

## Acknowledgments
- GTSRB dataset creators
- DS 6050 course staff

---

For questions or contributions, please contact the project authors.