# Classification Metrics from Confusion Matrix

## Confusion Matrix Summary
```
                    True Class
Predicted    | chili_antracnose | chili_healthy | background | Total
-------------|------------------|---------------|------------|-------
chili_antracnose |      13       |       0       |     7      |  20
chili_healthy    |       0       |     104       |     2      | 106
background       |       4       |       1       |     0      |   5
Total            |      17       |     105       |     9      | 131
```

## Per-Class Metrics

### 1. Chili Antracnose
- **TP** = 13 (correctly predicted as chili_antracnose)
- **FP** = 7 (incorrectly predicted as chili_antracnose)
- **FN** = 4 (actually chili_antracnose but predicted as other classes)
- **TN** = 104 + 2 + 1 + 0 = 107 (correctly predicted as not chili_antracnose)

**Metrics:**
- **Precision** = TP/(TP+FP) = 13/(13+7) = 13/20 = **0.650 (65.0%)**
- **Recall** = TP/(TP+FN) = 13/(13+4) = 13/17 = **0.765 (76.5%)**
- **F1 Score** = 2×(Precision×Recall)/(Precision+Recall) = 2×(0.650×0.765)/(0.650+0.765) = **0.703 (70.3%)**
- **Accuracy** = (TP+TN)/(TP+TN+FP+FN) = (13+107)/(13+107+7+4) = 120/131 = **0.916 (91.6%)**

### 2. Chili Healthy
- **TP** = 104 (correctly predicted as chili_healthy)
- **FP** = 2 (incorrectly predicted as chili_healthy)
- **FN** = 1 (actually chili_healthy but predicted as other classes)
- **TN** = 13 + 7 + 4 + 0 = 24 (correctly predicted as not chili_healthy)

**Metrics:**
- **Precision** = TP/(TP+FP) = 104/(104+2) = 104/106 = **0.981 (98.1%)**
- **Recall** = TP/(TP+FN) = 104/(104+1) = 104/105 = **0.990 (99.0%)**
- **F1 Score** = 2×(0.981×0.990)/(0.981+0.990) = **0.986 (98.6%)**
- **Accuracy** = (TP+TN)/(TP+TN+FP+FN) = (104+24)/(104+24+2+1) = 128/131 = **0.977 (97.7%)**

### 3. Background
- **TP** = 0 (correctly predicted as background)
- **FP** = 4 + 1 = 5 (incorrectly predicted as background)
- **FN** = 7 + 2 = 9 (actually background but predicted as other classes)
- **TN** = 13 + 104 = 117 (correctly predicted as not background)

**Metrics:**
- **Precision** = TP/(TP+FP) = 0/(0+5) = **0.000 (0.0%)**
- **Recall** = TP/(TP+FN) = 0/(0+9) = **0.000 (0.0%)**
- **F1 Score** = 2×(0.000×0.000)/(0.000+0.000) = **0.000 (0.0%)**
- **Accuracy** = (TP+TN)/(TP+TN+FP+FN) = (0+117)/(0+117+5+9) = 117/131 = **0.893 (89.3%)**

## Overall Metrics

### Macro-Average (Average across classes)
- **Precision** = (0.650 + 0.981 + 0.000)/3 = **0.544 (54.4%)**
- **Recall** = (0.765 + 0.990 + 0.000)/3 = **0.585 (58.5%)**
- **F1 Score** = (0.703 + 0.986 + 0.000)/3 = **0.563 (56.3%)**

### Micro-Average (Weighted by support)
- **Overall Accuracy** = (13 + 104 + 0)/131 = 117/131 = **0.893 (89.3%)**

### Weighted Average (Weighted by class frequency)
- **Precision** = (0.650×17 + 0.981×105 + 0.000×9)/131 = **0.899 (89.9%)**
- **Recall** = (0.765×17 + 0.990×105 + 0.000×9)/131 = **0.893 (89.3%)**
- **F1 Score** = (0.703×17 + 0.986×105 + 0.000×9)/131 = **0.881 (88.1%)**

## Summary Table

| Class | Precision | Recall | F1 Score | Accuracy | Support |
|-------|-----------|--------|----------|----------|---------|
| Chili Antracnose | 65.0% | 76.5% | 70.3% | 91.6% | 17 |
| Chili Healthy | 98.1% | 99.0% | 98.6% | 97.7% | 105 |
| Background | 0.0% | 0.0% | 0.0% | 89.3% | 9 |
| **Macro Avg** | **54.4%** | **58.5%** | **56.3%** | - | 131 |
| **Weighted Avg** | **89.9%** | **89.3%** | **88.1%** | - | 131 |
| **Overall Accuracy** | - | - | - | **89.3%** | 131 |

## Key Observations

1. **Chili Healthy** performs excellently with very high precision, recall, and F1 scores
2. **Chili Antracnose** has moderate performance with room for improvement
3. **Background** class performs very poorly - the model fails to detect any background samples correctly
4. The overall accuracy is good at 89.3%, but this is heavily influenced by the dominant "chili healthy" class
5. The poor performance on the "background" class significantly impacts the macro-averaged metrics
