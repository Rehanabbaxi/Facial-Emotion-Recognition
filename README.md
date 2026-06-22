# Facial Emotion Recognition

A machine learning / computer vision project for detecting facial expressions and classifying them into emotions from images or video frames.

## Overview

This project aims to recognize human emotions from facial images using computer vision and machine learning techniques. It can be used in applications such as:

- Human-computer interaction
- Sentiment analysis
- Smart surveillance
- Customer experience analytics
- Accessibility tools

## Features

- Detects faces from images or video input
- Classifies facial expressions into emotion categories
- Can be extended for real-time emotion recognition
- Easy to integrate into other computer vision pipelines

## Technologies Used

- Python
- OpenCV
- Machine Learning / Deep Learning
- NumPy
- TensorFlow / Keras or PyTorch  *(update based on your implementation)*

## Project Structure

```bash
.
├── wieghts/                    # Pretrained model weights (see below)
│   ├── ckpt_cnn_baseline.pt    # Model 1 — custom CNN baseline
│   ├── ckpt_cnn_focal_sgd.pt   # Model 2 — custom CNN (focal loss + SGD)
│   ├── ckpt_mobilenetv2_tl.pt  # Model 3 — MobileNetV2 transfer learning
│   └── best_fer_model.pt       # Final best model (used for inference)
├── FER_Colab_Notebook.ipynb    # End-to-end training + inference notebook
└── README.md
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/Rehanabbaxi/Facial-Emotion-Recognition.git
cd Facial-Emotion-Recognition
```

### 2. Create a virtual environment

```bash
python -m venv venv
```

#### Activate the virtual environment

**Windows:**
```bash
venv\Scripts\activate
```

**macOS/Linux:**
```bash
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

## Usage

If the project includes a training script:

```bash
python train.py
```

If the project includes an inference or demo script:

```bash
python app.py
```

Or run the notebook:

```bash
jupyter notebook
```

## Pretrained Weights

The [`wieghts/`](wieghts) folder contains the trained weights for **all three models**
benchmarked in the notebook, plus the final best model:

| File | What it is |
|------|------------|
| `ckpt_cnn_baseline.pt`   | Model 1 — custom CNN baseline (AdamW + cosine LR + weighted CE) |
| `ckpt_cnn_focal_sgd.pt`  | Model 2 — custom CNN (focal loss + SGD + weighted sampler) |
| `ckpt_mobilenetv2_tl.pt` | Model 3 — MobileNetV2 transfer learning |
| **`best_fer_model.pt`**  | **Final best model** — self-contained (weights + class names + config); this is the one the inference cells load |

> The three `ckpt_*.pt` files are raw `state_dict`s for each experiment.
> **`best_fer_model.pt`** is the final pick and is fully self-describing, so
> inference can rebuild the exact architecture from it.

## Running in Google Colab

1. Open `FER_Colab_Notebook.ipynb` in Google Colab and set
   **Runtime → Change runtime type → T4 GPU**.
2. **To retrain from scratch:** just run all cells top to bottom.
3. **To skip training and run inference with the provided weights:**
   - Upload the weights into Colab. Easiest is to clone this repo inside Colab:
     ```python
     !git clone https://github.com/Rehanabbaxi/Facial-Emotion-Recognition.git
     ```
     (or drag the files from `wieghts/` into Colab's file browser under `/content/`).
   - Point the inference loader at the best model before running the
     **Section 10 — Inference** cell:
     ```python
     SAVE_PATH = '/content/Facial-Emotion-Recognition/wieghts/best_fer_model.pt'
     ```
   - Then run the inference cells (Section 10 — upload an image, Section 11 — webcam).

## Dataset

This project uses facial expression data for training and evaluation.  
If you used a public dataset, list it here, for example:

- FER-2013
- CK+
- RAF-DB

## Model

If applicable, describe your model here:

- Architecture: CNN / transfer learning / custom model
- Input size: e.g. `48x48` grayscale images
- Output classes: e.g. `angry`, `happy`, `sad`, `neutral`, etc.

## Results

Add your results here, such as:

- Training accuracy
- Validation accuracy
- Confusion matrix
- Sample predictions

Example:

- Accuracy: 92%
- Validation Loss: 0.18

## Future Improvements

- Improve real-time detection speed
- Support more emotion categories
- Enhance robustness under different lighting conditions
- Deploy as a web or mobile application

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository
2. Create a new branch
3. Make your changes
4. Submit a pull request

## License

Add your license information here.

## Acknowledgements

- Dataset providers
- Open-source libraries such as OpenCV and TensorFlow
- Any tutorials or references used during development
