# Predicting Student Misconceptions in Mathematics

## Project Overview
This project focuses on predicting student misconceptions in mathematics using machine learning models. By analyzing diagnostic question responses, the project aims to identify and address specific areas of misunderstanding, empowering educators to provide targeted interventions.

---

## Dataset

### Sources
- **Train Dataset (`train.csv`)**: Contains labeled data with 1,869 rows.
- **Test Dataset (`test.csv`)**: Contains unlabeled data with 467 rows.
- **Misconception Mapping (`misconception_mapping.csv`)**: Maps each `MisconceptionId` to its description.

### Schema
| Column Name       | Description                                     |
|-------------------|-------------------------------------------------|
| `QuestionId`      | Unique identifier for each question.            |
| `ConstructId`     | Identifier for the concept being tested.        |
| `ConstructName`   | Descriptive name for the concept.               |
| `SubjectId`       | Identifier for the subject area.                |
| `SubjectName`     | Descriptive name for the subject.               |
| `CorrectAnswer`   | Correct answer to the question (A, B, C, or D). |
| `QuestionText`    | Full text of the question.                      |
| `AnswerAText`     | Text for answer option A.                       |
| `AnswerBText`     | Text for answer option B.                       |
| `AnswerCText`     | Text for answer option C.                       |
| `AnswerDText`     | Text for answer option D.                       |
| `MisconceptionAId`| Misconception ID for answer A (if incorrect).    |
| `MisconceptionBId`| Misconception ID for answer B (if incorrect).    |
| `MisconceptionCId`| Misconception ID for answer C (if incorrect).    |
| `MisconceptionDId`| Misconception ID for answer D (if incorrect).    |

---

## Preprocessing
1. **Handling Missing Values**:
   - Replaced missing misconception values with `0`.
   - Removed rows with no misconceptions.
2. **Class Balancing**:
   - Used oversampling and undersampling to address imbalanced classes.
3. **Feature Engineering**:
   - Combined question and answer text into a `CombinedText` column.
   - Applied TF-IDF vectorization with 5,000 features.

---

## Model Development

### Models Implemented
- **Random Forest**
- **Gradient Boosting**
- **Logistic Regression**

### Training and Validation
- **Training Data**: 80% of the dataset (173 samples).
- **Validation Data**: 20% of the dataset (44 samples).
- **Evaluation Metrics**:
  - Accuracy
  - Precision
  - Recall
  - F1 Score

---

## Performance Metrics

| Model               | Accuracy | Precision | Recall | F1 Score |
|---------------------|----------|-----------|--------|----------|
| Random Forest       | 0.0379   | 0.0417    | 0.0379 | 0.0379   |
| Gradient Boosting   | 0.0455   | 0.0352    | 0.0455 | 0.0372   |
| Logistic Regression | 0.0152   | 0.0027    | 0.0152 | 0.0042   |

---

## SHAP Analysis
- **Feature Importance**:
  - Identified key features contributing to predictions.
  - Example:
    - High impact: `Sharing in a Ratio`, `Algebraic Simplification`
- **Visualization**:
  - Summary plots for global importance.
  - Force plots for individual predictions.

---

## Challenges and Limitations
- **Challenges**:
  - Highly imbalanced data.
  - Limited dataset size for generalization.
- **Limitations**:
  - Modest performance metrics.
  - Difficulty handling sparse misconception classes.

---

## Recommendations
1. Experiment with advanced models like transformer-based architectures (e.g., BERT).
2. Increase dataset size using synthetic data augmentation.
3. Perform hyperparameter tuning for optimized model performance.
4. Explore ensemble methods to combine the strengths of multiple models.

---

## How to Run the Project

### Prerequisites
1. Python 3.8 or later.
2. Required libraries:
   - pandas
   - numpy
   - scikit-learn
   - matplotlib
   - seaborn
   - shap

### Installation
```bash
pip install -r requirements.txt
```

### Steps to Execute
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/misconception-prediction.git
   cd misconception-prediction
   ```
2. Run the preprocessing script:
   ```bash
   python preprocess_data.py
   ```
3. Train the models:
   ```bash
   python train_models.py
   ```
4. Evaluate the models:
   ```bash
   python evaluate_models.py
   ```
5. Visualize SHAP analysis:
   ```bash
   python shap_analysis.py
   ```

---

## Authors
- **Hemanth Kumar Peddameti**

---

## Acknowledgments
- **Tools Used**: Python, Scikit-learn, SHAP.
- **Special Thanks**: SHAP documentation, Scikit-learn guides.

---

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
