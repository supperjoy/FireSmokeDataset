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
Fire regions are defined as visible flames with distinct color characteristics (e.g., red, orange, and yellow) and high luminance. Only regions that exhibit clear combustion characteristics are annotated, while fire-like objects such as sunsets, lamps, or reflections are not labeled as fire.
﻿
### 2. Smoke Definition
Smoke is defined to include both dense and thin forms with diffuse boundaries, typically exhibiting semi-transparent and irregular shapes with gray or white tones. Even low-contrast smoke is annotated provided that it is visually distinguishable.
﻿
### 3. Ambiguous Cases
Ambiguous cases such as fog, steam, and clouds are generally excluded from smoke annotations to avoid introducing noisy labels. Annotations are only assigned when there is clear evidence of a combustion source, such as co-occurrence with fire or identifiable smoke-like motion patterns originating from burning objects. In uncertain cases, a conservative strategy is adopted, and no annotation is assigned.
﻿
### 4. Bounding Box Rules
Bounding boxes are required to tightly cover the visible extent of the target while minimizing unnecessary background. For objects with clear boundaries, annotations should closely follow the object shape. For diffuse or irregular regions such as smoke, bounding boxes are allowed to cover the main visible area without requiring precise alignment with unclear boundaries.
﻿
### 5. Exclusion Rules
Samples that are extremely unclear, heavily occluded, or difficult to interpret are excluded from annotation to reduce noisy labels. In cases where the presence of fire or smoke cannot be confidently determined, no annotation is assigned.
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
- Train / Test / Validation = 7 : 2 : 1
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
| Epochs | 200 |
| Optimizer | SGD |
| Learning rate | 0.01 |
| Momentum | 0.937 |
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
