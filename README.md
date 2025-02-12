### README: Mushroom Classification with Random Forest  

# Mushroom Classification  

This project focuses on classifying mushrooms as **edible (e)** or **poisonous (p)** using a **Random Forest Classifier**. Given the risks associated with consuming wild mushrooms, an accurate classification model can help prevent accidental poisoning.  

## Dataset  

The dataset consists of multiple **categorical features**, each describing different characteristics of mushrooms, such as **appearance, structure, odor, and habitat**. The target variable indicates whether a mushroom is **edible or poisonous**.  

## Installation and Dependencies  

Ensure you have the necessary libraries installed before running the project:  

```bash
pip install numpy pandas scikit-learn
```

## Data Preprocessing  

1. **Label Encoding**: Since all features are categorical, we apply **Label Encoding** to convert them into numerical values.  
2. **Train-Test Split**: The dataset is divided into training and testing sets for model evaluation.  
3. **Feature Engineering**: The training and test sets are merged before encoding to ensure consistency.  

## Model Training  

We use a **Random Forest Classifier** with the following parameters:  

- **n_estimators**: 100 (number of trees)  
- **bootstrap**: True (random sampling with replacement)  
- **oob_score**: True (out-of-bag score for validation)  

```python
from sklearn.ensemble import RandomForestClassifier

model = RandomForestClassifier(n_estimators=100, bootstrap=True, oob_score=True)
model.fit(X_train, y_train)
```

## Model Evaluation  

The model is evaluated using:  

- **Accuracy Score**: Measures overall classification accuracy.  
- **Recall Score**: Ensures the model correctly identifies poisonous mushrooms.  

```python
from sklearn.metrics import accuracy_score, recall_score

accuracy = accuracy_score(y_test, y_pred)
recall = recall_score(y_test, y_pred, pos_label=1)

print(f"Accuracy: {accuracy}")
print(f"Recall: {recall}")
```

## Predictions  

Once trained, the model predicts whether a given mushroom is edible or poisonous:  

```python
prediction = pd.DataFrame({'class': model.predict(test)})
prediction['class'] = prediction['class'].replace({1: 'p', 0: 'e'})
```

## Conclusion  

This model provides a **highly accurate** way to classify mushrooms, potentially surpassing human expertise. While **mushroom hunting** requires deep knowledge, this **AI-driven model** automates the process, reducing the risk of consuming poisonous mushrooms.  

## Files  

- **train.csv** – Training dataset  
- **test.csv** – Test dataset  
- **mushroom_classification.ipynb** – Project code  

## Collaboration  

If you have ideas to improve the model, feel free to contribute! 🚀
