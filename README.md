# Alzheimer's Disease Classification Using a Custom CNN Model
This project aims to detect MRI-based Alzheimer’s Disease Stage with Deep Learning Techniques


## Methodology
### Preprocessing – Dealing with Imbalanced Dataset
**Implementation of Resampling Techniques**  
- **Goal**: Adjust the dataset so that each class has an equal number of samples to ensure balanced learning.
- **Outcome**: Prevents the model from overlooking or underperforming on the "Moderate Demented" stage.

**Randomization to Prevent Sequence Bias**  
- **Goal**: Randomize the order of data to prevent any sequence bias that might impact training.
- **Outcome**: Ensures that the model’s learning is based on intrinsic characteristics, not the order of data.

### Model – Customized CNN Architecture
The model is a sequential Convolutional Neural Network (CNN) specifically designed for image classification tasks. Below is a detailed breakdown of the architecture:

#### Input Layer
- **Input Image Specifications**: 224x224 pixels with 3 channels (RGB).

#### Convolutional Layers
1. **First Layer**: 32 filters (3x3), without bias, to extract low-level features.
2. **Second Layer**: 64 filters (3x3) to capture complex features.
3. **Third and Fourth Layers**: 128 filters each, for deeper feature extraction.

**ReLU Activation** is applied after each layer for non-linear learning.

#### Pooling Layers
**MaxPooling** with a 2x2 window is used after each convolutional layer to reduce spatial dimensions.

#### Regularization Techniques
**Dropout** at 0.5 rate is used post-convolution and pooling to prevent overfitting.

#### Dense Layers
- **Flattening** transforms 2D feature maps to 1D vectors.
- **Fully Connected Layer** with 512 neurons using ReLU activation integrates learned features.

#### Output Layer
- **Dense Layer**: 4 units with a softmax activation function for multi-class classification.

**Kernel and Activity Regularizers** are used in the dense layer for L1 and L2 regularization to maintain simpler models.

### Loss – Custom Loss Function
- **Goal**: Enhance the model's robustness, particularly at challenging classification margins.
- **Function Details**: Transforms true labels (`y_true`) to a new scale (`y_true_transformed = 2 * y_true - 1`) to align model outputs with expected margins.

### Model Test Results
**Performance Metrics**
- **Test Loss**: 4.0127
- **Test Accuracy**: 78.22%

**Confusion Matrix Analysis**
- **True Positives**:
  - Non-Demented: 159
  - Very Mild Demented: 148
  - Mild Demented: 170
  - Moderate Demented: 167

**High Confusion Areas**: Notable confusion between adjacent stages, particularly between Non-Demented and Very Mild Demented, as well as Mild Demented and Moderate Demented.

### Conclusion
- The model demonstrates a competent level of accuracy (78.22%) in classifying the stages of Alzheimer's disease.
- Further model tuning and more balanced datasets could reduce misclassification rates.
