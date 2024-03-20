# BLOB

BLOB - Brain Lesion Observation Brigade - AI project for the University of Bristol, involving a brain tumor detecting algorithms. It particularly focuses on eliminating false negatives. 

## Abstract (from Report)

This report focuses on tumor detection in brain scans, with a critical emphasis on minimising false negatives, where a positive result indicates the presence of a tumor. This is crucial as the system is designed to serve as an initial screening tool that flags potential tumors, enabling pathologists to concentrate their efforts on a more narrowed selection of cases. To improve detection accuracy, a skull stripping (SS) model using a U-Net architecture isolates the brain tissue. This is followed by a Binary Classification (BC) model based on a Sequential architecture for identifying tumors. The effectiveness of SS as a preprocessing step is validated by its contribution to improving model accuracy whilst reducing false negatives. Additionally, the outcomes presented highlight the increasing effectiveness of these approaches in managing diagnostic tasks, successfully achieving a model with no false negatives and satisfactory accuracy.

# Installation Instructions

## Prerequisites
Ensure you have Python 3.10.9 and Pip installed on your system.

## Setup
1. **Create and activate a virtual environment:**

    - For Windows:
    ```
    python -m venv myenv
    myenv\Scripts\activate
    ```

    - For macOS and Linux:
    ```
    python -m venv myenv
    source myenv/bin/activate
    ```

2.  **Install dependencies:**
```
pip install tensorflow numpy opencv-python-headless scikit-learn matplotlib seaborn pandas scikit-image pillow scipy
```
# Usage of Pre-Trained Model

The pre-trained models discussed in the report are stored in this repository. The skull stripping model is `model_binary_SSM.h5` and the binary classification is `model_binary.h5`

## Skull Stripping Model
1. ** Import the necessary module:

```python
from tensorflow.keras.models import load_model
import matplotlib.pyplot as plt
```

2. ** Load Model**:
   Use the `load_model` function, passing the path, if necessary, to your `model_binary_SSM.h5` file:

```python
model_SSM = load_model('model_binary_SSM.h5') # make sure .py file is in same directory as .h5 or specify path
```

3. **Using the model**:
   The skull stripping model is designed to process CT scans of the brain, requiring specific input formats:
    - **Input Image**: A CT scan image of the brain, expected to be in the shape of `(128, 128, 3)`. 

    - **Input Mask**: A template mask in binary form, with a shape of `(128, 128, 1)`, which indicates areas of interest (e.g., the brain) to be stripped from the skull. If you do not have a custom mask, a default one can be used, which is available in the `skull_stripping.py` script under the variable `image_template_masks_array`.

```python
predictions = model_SSM.predict(image, mask)
plt.imshow(predictions)
plt.axis('off')
plt.show()
```
## Binary Classification Model
1. ** Import the necessary module:

```python
from tensorflow.keras.models import load_model
```

2. ** Load Model**:
   Same as before but with the file `model_binary.h5` file:

```python
model_SSM = load_model('model_binary.h5') # make sure .py file is in same directory as .h5 or specify path
```

3. **Using the model**:
   The Binary Classification requires only the input image, preferably for better results, preprocessed with SSM:
    - **Input Image**: A CT scan image of the brain, expected to be in the shape of `(128, 128, 3)`. 

```python
predictions = model_SSM.predict(image, mask)
print(predictions) # 0 for no tumor, 1 for tumor
```

# Dataset 

Dataset obtained and stored in `Training` and `Testing` is from:

```
@misc{sartaj_bhuvaji_ankita_kadam_prajakta_bhumkar_sameer_dedge_swati_kanchan_2020,
	title={Brain Tumor Classification (MRI)},
	url={https://www.kaggle.com/sartajbhuvaji/brain-tumor-classification-mri},
	DOI={10.34740/KAGGLE/DSV/1183165},
	publisher={Kaggle},
	author={Sartaj Bhuvaji and Ankita Kadam and Prajakta Bhumkar and Sameer Dedge and Swati Kanchan},
	year={2020}
}
```

# Features
## `Mask_Training` and `Mask_Training`
Located the 80 hand drawn mask for SSM.

## `New_Mask_Training` and `New_Mask_Training`
Result of SSM for the entirety of the dataset.

## `notebook_initial_model.ipynb`
Notebook used to develop the binary classification. 

## `notebook_multiclass_model.ipynb`
Notebook used to develop the multiclass classification, eventually unused in the report.

## `skull_stripping.ipynb`
Notebook used to develop the skull stripping model.

# Declaration of AI

  AI models (such as ChatGPT, CoPilot and Grammarlay) have been used as an assistance tool when coding models,  understanding python packages and increasing readibility of code.  It was also used to assist in improving grammar and readability when writting up the report.
