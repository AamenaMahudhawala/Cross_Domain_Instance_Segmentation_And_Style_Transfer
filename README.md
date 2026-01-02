

<h1 align = "center"> Cross-Domain Instance Segmentation & Style Transfer for Industrial Parts</h1>

<div align="right">
Aamena Mahudhawala
</div>

-----

## Project Overview

This project addresses the challenge of automated defect detection in industrial manufacturing under varying environmental conditions. The core objective is to train a robust Instance Segmentation model (Mask R-CNN) that performs well not only on standardized factory images (Domain A) but also on noisy, non-uniform real-world images (Domain B).

**The Pipeline:**

1.  **Baseline Training:** Train Mask R-CNN on **Domain A** (Uniform Illumination).
2.  **Domain Simulation:** Generate **Domain B** (Target) by introducing synthetic artifacts (noise, blur, lighting shifts).
3.  **Domain Adaptation:** Bridge the domain gap using Style Transfer/Augmentation techniques (CycleGAN).
4.  **Evaluation:** Compare segmentation performance (mAP) across domains.

-----

##  Dataset

This project uses the NEU-Seg dataset.

  * **Source:** [Roboflow - NEU-Seg Dataset](https://universe.roboflow.com/school-4pxkq/neu-seg)
  * **Note:** Sample subsets of the data are included in the `datasets/` folder for demonstration purposes.

-----

##  Directory Structure

```text
Cross_Domain_Instance_Segmentation_&_Style_Transfer/
│
├── code
│   ├── BASERCNN.ipynb                # Notebook to train the Mask R-CNN model
│   ├── CompletePipeLine.ipynb        # MAIN DEMO: Translation
│   ├── CycleGANtrain.ipynb           # Notebook used to train CycleGAN (Reference)
│   ├── EvaluationOFPipeline.ipynb    # Notebook to evaluate mAP metrics
│   ├── Model                         # Pre-trained Mask R-CNN model (Best Weights)   
│   └── results/
│       ├── visual_comparisons/       # Side-by-side images (Raw vs Enhanced)
│       └── full_metrics_comparison.png # Bar chart showing mAP improvement
│
├── datasets/
│   ├── NEU-seg-DOMAIN_A2/            # Clean/Source Domain 
│   ├── NEU-seg-DOMAIN_B2OR/          # Messy/Target Domain 
│   └── DomainB_Enhanced/             # Enhanced/Translated Domain 
│
├── Cross-Domain_Instance_Segmentation_&_Style_Transfer.pdf  # Full Project Report
│
└── requirements.txt                  # Python dependencies
```

-----

##  Setup & Installation

1.  **Prerequisites:** Ensure Python 3.9+ and PyTorch are installed.
2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

-----


## Results Summary

The Domain Adaptation strategy significantly improved performance on the noisy target domain.

| Metric | Without Adaptation (Raw Domain B) | With Adaptation (Enhanced Domain B) | Improvement |
| :--- | :---: | :---: | :---: |
| **BBox mAP** | 42.17% | **44.69%** | **+2.52%** |
| **Segm mAP** | 34.47% | **36.07%** | **+1.60%** |
| **AP50 (Box)**| 70.48% | **75.69%** | **+5.21%** |
| **AP50 (Segm)**| 65.99% | **70.26%** | **+4.27%** |

*For full details, please refer to the included PDF report.*

-----
