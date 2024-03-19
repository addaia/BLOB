# BLOB

BLOB - Brain Lesion Observation Brigade - AI project for the University of Bristol, involving a brain tumor detecting algorithms. It particularly focuses on eliminating false negatives. 

## Abstract (from Report)

This report focuses on tumor detection in brain scans, with a critical emphasis on minimising false negatives, where a positive result indicates the presence of a tumor. This is crucial as the system is designed to serve as an initial screening tool that flags potential tumors, enabling pathologists to concentrate their efforts on a more narrowed selection of cases. To improve detection accuracy, a skull stripping (SS) model using a U-Net architecture isolates the brain tissue. This is followed by a Binary Classification (BC) model based on a Sequential architecture for identifying tumors. The effectiveness of SS as a preprocessing step is validated by its contribution to improving model accuracy whilst reducing false negatives. Additionally, the outcomes presented highlight the increasing effectiveness of these approaches in managing diagnostic tasks, successfully achieving a model with no false negatives and satisfactory accuracy.

# Installation Instructions

## Prerequisites
Ensure you have Python 3.x and Pip installed on your system.

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




