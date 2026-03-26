# EFS-DETR Dataset and Reproducibility Resources
﻿
This repository provides the annotation guidelines, data processing pipeline, and training configurations for the EFS-DETR framework.
﻿
Due to licensing constraints of web-sourced images, only a subset of the dataset is released. The following resources are provided to facilitate reproducibility.
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
- Fire-like objects (e.g., sunset, lamps, reflections) are NOT labeled as fire.
﻿
### 2. Smoke Definition
- Smoke includes both dense and thin smoke with diffuse boundaries.
- It is typically characterized by semi-transparent, irregular shapes with gray or white tones.
- Low-contrast smoke is still annotated if visually distinguishable.
﻿
### 3. Ambiguous Cases
- Fog, steam, and clouds are NOT labeled as smoke.
- Exceptions:
  - When co-occurring with fire
  - When showing clear smoke-like behavior
﻿
### 4. Bounding Box Rules
- Bounding boxes should tightly cover the visible region.
- For large or irregular smoke, a single bounding box can be used.
﻿
### 5. Multi-object Scenarios
- Each fire or smoke instance is annotated separately.
﻿
### 6. Exclusion Rules
- Extremely unclear or heavily occluded targets are excluded.
﻿
---
﻿
## ⚙️ Data Processing Pipeline
﻿
The dataset is constructed through a multi-stage pipeline:
﻿
### 1. Data Collection
- Public fire/smoke datasets
- Open web sources (for research use only)
- Self-collected images
﻿
### 2. Data Filtering
- Remove low-quality images (blurred, overexposed)
- Remove irrelevant samples
﻿
### 3. Deduplication
- Near-duplicate images are removed using perceptual hashing
﻿
### 4. Annotation
- Annotated using LabelImg
- Following the annotation guidelines above
﻿
### 5. Quality Control
- Verified by at least two annotators
- Conflicts resolved through discussion
﻿
### 6. Data Split
- Train / Val / Test = 7 : 2 : 1
- Scene-level separation:
  - Images from the same scene/video are kept in the same subset
- Prevents data leakage
﻿
### 7. Data Augmentation (Training Only)
- Random flipping
- Scaling
- Color jittering
- (Optional: Mosaic augmentation)
﻿
---
﻿
## 🧠 Training Configuration
﻿
All models are trained under unified settings:
﻿
- Input size: 640 × 640
- Batch size:
  - Training: 32
  - Inference: 1
- Epochs: 200
- Optimizer: SGD (or AdamW)
- Initial learning rate: 0.01
- Weight decay: 5e-4
- Learning rate schedule: cosine decay (or step decay)
﻿
### Inference Setting
- Batch size = 1
- Includes:
  - Forward inference
  - Decoding
  - Non-maximum suppression (NMS)
- Excludes:
  - Data loading
﻿
---
﻿
## 📊 Dataset Availability
﻿
- A subset of the dataset is publicly released:
  - Self-collected data
  - Redistributable images
﻿
---
﻿
## 🔁 Reproducibility
﻿
To reproduce the results:
﻿
1. Follow the annotation guidelines
2. Apply the same data processing pipeline
3. Use the provided training configuration
﻿
---
﻿
## 📌 Notes
﻿
- Experiments are also conducted on public datasets to validate generalization.
- All models are evaluated under consistent settings for fair comparison.
﻿
---
﻿
## 📬 Contact
﻿
For additional resources or questions, please contact the authors.
