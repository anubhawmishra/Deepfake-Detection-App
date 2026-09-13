# Deepfake Detection System

A desktop application (Tkinter GUI + CNN backend) that detects whether an
image or video has been manipulated (deepfake) or is authentic. Built as a
final-year Computer Engineering project at Sinhgad Institute of Technology
and Science, Pune.

This project is based on the research paper **"Guarding Authenticity: A
Deepfake Detection System"**, co-authored by Prof. N. R. Thorat, Prajwal
Mohite, Anubhaw Mishra, and Rohit Sawant — published in:

- **JETIR**, Vol. 11, Issue 5, May 2024 — [docs/Implementation_Paper_JETIR2405D71.pdf](docs/Implementation_Paper_JETIR2405D71.pdf)
- **IJSREM**, Vol. 8, Issue 5, May 2024, DOI: [10.55041/IJSREM34789](https://doi.org/10.55041/IJSREM34789) — [docs/Survey_Paper.pdf](docs/Survey_Paper.pdf)

## Architecture

```
Input Image/Video Dataset → Preprocessing → Feature Extraction → CNN Model Training → Prediction (Real / Tampered / Fake)
```

The model is a Deep Convolutional Neural Network (D-CNN) trained with the
Adam optimizer and binary cross-entropy loss, reporting >95% accuracy in
the paper.

## Tech Stack

- **Frontend:** Tkinter (Python GUI)
- **Backend:** Python, OpenCV
- **Model:** CNN built with Keras/TensorFlow
- **Storage:** SQLite (user login/registration)

## Project Structure

```
deepfake-detection-app/
├── Window.py            # App entry point (splash screen)
├── GUI_main.py           # Welcome screen (login/register)
├── login.py              # Login form
├── registration.py       # Registration form
├── GUI_Master_old.py     # Image upload + preprocessing + CNN prediction
├── GUI_Master_New.py     # Video upload + prediction + model training
├── CNNModel.py           # CNN architecture + training (image model)
├── Train_FDD_cnn.py      # CNN architecture + training (video model)
├── model_CNN.py          # Alternate/reference model script
├── video_to_frames.py    # Utility to extract frames from video
├── docs/                 # Published research papers
├── screenshots/          # Project diagrams / theme paper
└── requirements.txt
```

## Setup

1. Clone the repo:
   ```bash
   git clone <your-repo-url>
   cd deepfake-detection-app
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. **Dataset:** This project trains on an image/video dataset (~5GB) that
   is not included in this repo due to size. Download it from:
   `[ADD YOUR GOOGLE DRIVE / KAGGLE LINK HERE]`

   Place it in the project root so the folder structure matches what
   `CNNModel.py` / `Train_FDD_cnn.py` expect (`training/`, `testing/`,
   `normal/`, `abnormal/` folders).

4. **Trained models:** `model1.h5` and `model2.h5` (used for prediction)
   are also not included. Either train them yourself using `CNNModel.py`
   / `Train_FDD_cnn.py`, or download pre-trained weights from:
   `[ADD LINK IF YOU HAVE ONE]`

5. **Note on paths:** Some scripts currently have hardcoded local paths
   (e.g. `C:/Users/...`). Update `basepath` variables in `CNNModel.py`
   and `Train_FDD_cnn.py` to match your local dataset location before
   training.

## Running the App

```bash
python Window.py
```

Flow: splash screen → Login/Register → select image or video →
preprocess → CNN prediction (Real / Tampered / Fake).

## Citation

If you reference this work, please cite:

> Thorat, N. R., Mohite, P., Mishra, A., & Sawant, R. (2024). Guarding
> Authenticity: A Deepfake Detection System. *International Journal of
> Scientific Research in Engineering and Management (IJSREM)*, 8(5).
> https://doi.org/10.55041/IJSREM34789

## Disclaimer

This is an academic project built for learning purposes. The login system
stores passwords in plaintext in SQLite and is not intended for
production/security-sensitive use.
