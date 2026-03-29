# EFS-DETR Dataset and Reproducibility Resources
﻿
This repository provides the annotation guidelines, data processing pipeline, and training configurations for the EFS-DETR framework.
﻿
Due to licensing constraints of web-sourced images, only a subset of the dataset is released. The provided resources aim to ensure transparency and facilitate reproducibility.
﻿
---
﻿
## 📌 Annotation Guidelines
﻿
All images are annotated with bounding boxes for two categories: **fire** and **smoke**.
﻿
### 1. Fire Definition
- Fire regions are defined as visible flames with distinct color (e.g., red, orange, yellow) and high luminance.
- Only regions with clear combustion characteristics are annotated.
- Fire-like objects (e.g., sunset, lamps, reflections) are **NOT** labeled as fire.
﻿
### 2. Smoke Definition
- Smoke includes both dense and thin smoke with diffuse boundaries.
- It is typically characterized by semi-transparent, irregular shapes with gray or white tones.
- Low-contrast smoke is still annotated if it is visually distinguishable.
﻿
### 3. Ambiguous Cases
- Fog, steam, and clouds are **NOT** labeled as smoke.
- Exceptions:
  - When co-occurring with fire
  - When exhibiting clear smoke-like patterns originating from combustion
﻿
### 4. Bounding Box Rules
- Bounding boxes should tightly cover the visible extent of the target.
- For large or irregular smoke regions, a single bounding box may be used to cover the main area.
﻿
### 5. Multi-object Scenarios
- Each fire or smoke instance is annotated separately.
﻿
### 6. Exclusion Rules
- Extremely unclear, heavily occluded, or ambiguous samples are excluded from annotation.
﻿
---
﻿
## ⚙️ Data Processing Pipeline
﻿
The dataset is constructed through a multi-stage data processing pipeline:
﻿
### 1. Data Collection
- Public fire/smoke datasets
- Open web resources (used strictly for research purposes)
- Self-collected images
﻿
### 2. Data Filtering
- Remove low-quality images (e.g., blurred, overexposed)
- Remove irrelevant or mislabeled samples
﻿
### 3. Deduplication
- Near-duplicate images are removed using perceptual hashing to reduce redundancy and prevent data leakage
﻿
### 4. Annotation
- Annotated using the LabelImg tool
- Following the annotation guidelines described above
﻿
### 5. Quality Control
- All annotations are verified by at least two annotators
- Disagreements are resolved through discussion to ensure consistency
﻿
### 6. Data Split
- Train / Validation / Test = 7 : 2 : 1
﻿
### 7. Data Augmentation (Training Only)
- Random horizontal flipping
- Random scaling
- Color jittering
- Mosaic augmentation
﻿
---
## 🧠 Training Configuration

| Item | Setting |
|------|--------|
| Input size | 640 × 640 |
| Batch size (train) | 32 |
| Batch size (test) | 1 |
| Epochs | 200 |
| Optimizer | SGD |
| Learning rate | 0.01 |
| Momentum | 0.9 |
| Weight decay | 5e-4 |﻿
---
﻿
## 📊 Dataset Availability
﻿
- A subset of the dataset is publicly released, including:
  - Self-collected data  
  - Publicly redistributable images  
﻿
- Web-sourced images are **not included** due to licensing restrictions.
﻿
---
﻿
## 🔁 Reproducibility
﻿
To reproduce the experimental results:
﻿
1. Follow the annotation guidelines provided in this repository  
2. Apply the same data processing pipeline  
3. Use the training configurations described above  
﻿
These resources are designed to enable consistent and reproducible implementation of the proposed method.
﻿
---
﻿
## 📌 Notes
﻿
- Additional experiments are conducted on public datasets to validate the generalization capability of the proposed method.  
- All models are evaluated under consistent hardware and software settings for fair comparison.  
﻿
---
﻿
## 📬 Contact
﻿
For access to the full dataset, please contact the authors.
