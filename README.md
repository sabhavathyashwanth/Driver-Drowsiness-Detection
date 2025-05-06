# Driver Drowsiness Detection Using InceptionV3

This project aims to detect driver drowsiness in real time by analyzing the driver’s eye state using deep learning techniques. It leverages a trained CNN model based on the InceptionV3 architecture to classify eye states (open or closed) and raises an alert if drowsiness is detected. The application is capable of real-time video monitoring using a webcam and serves as a proactive measure to prevent accidents caused by fatigue.

---

## Project Overview

Drowsiness behind the wheel is one of the leading causes of road accidents. This system is designed to monitor a driver's eye state in real time and determine whether the eyes are closed for an extended period, which could indicate drowsiness. If detected, an alert is triggered to wake the driver or draw their attention back to the road.

---

## Workflow Summary

1. **Data Preparation**  
   - Preprocessing of the image dataset containing "open eyes" and "closed eyes".
   - Normalization and labeling of images.
   - Directory structuring for model training.

2. **Model Training**  
   - A transfer learning approach is used with the InceptionV3 architecture.
   - Fine-tuning is applied to classify eye states.
   - Model is saved for real-time inference.

3. **Real-Time Monitoring**  
   - Webcam is used to capture frames.
   - Eyes are detected and cropped using OpenCV.
   - The trained model classifies the eye state per frame.
   - If the model detects closed eyes over consecutive frames, it triggers an alarm to alert the driver.

4. **Application Interface**  
   - A minimal `app.py` script is provided for deployment or integration into a GUI/web framework if needed.

---

## File Structure

```
Driver-Drowsiness-Detection/
│
├── Data Preparation_part-1.ipynb      # Image preprocessing and dataset setup
├── Model Training_part-2.ipynb        # Training InceptionV3 model on eye state data
├── Main_part-3.ipynb                  # Real-time drowsiness detection using webcam
├── app.py                             # App interface or wrapper (optional deployment entry)
├── models/
│   └── drowsiness_model.h5            # Trained eye state detection model (output of part-2)
├── haarcascades/
│   └── haarcascade_eye.xml            # Used to detect eyes in webcam frames
├── alarm.wav                          # Sound file for alert
```

---

## Technologies Used

- **Python** – Main programming language
- **OpenCV** – Face and eye detection using Haar cascades
- **TensorFlow / Keras** – Deep learning framework for model training and inference
- **InceptionV3** – Pre-trained CNN model used for eye state classification
- **NumPy, Pandas** – Data handling
- **Matplotlib, Seaborn** – Visualization during training
- **PyGame / Playsound** – To trigger audio alert

---

## How to Run

### 1. Environment Setup

Install required packages using:

```bash
pip install opencv-python tensorflow keras numpy pygame
```

### 2. Model Training

Run the notebook `Model Training_part-2.ipynb` after preparing data with `Data Preparation_part-1.ipynb`. It will save a trained model (`drowsiness_model.h5`).

### 3. Real-Time Detection

Run `Main_part-3.ipynb` to start real-time monitoring via webcam.

Alternatively, you can run the app interface using:

```bash
python app.py
```

Ensure:
- Webcam is accessible
- Trained model is available at the specified path
- Haar cascade file for eye detection is in place
- `alarm.wav` is in the working directory

---

## Model Details

- Architecture: InceptionV3 (Transfer Learning)
- Input: Eye-region images (resized to 224x224)
- Output: Binary classification (Open, Closed)
- Performance: Evaluated using accuracy and loss plots during training

---

## Limitations & Future Scope

- Currently detects only eye-based drowsiness (no yawning or head tilt).
- Detection might be affected by lighting conditions or obstructions (e.g., glasses).
- Future improvements could include:
  - Incorporation of multiple facial cues
  - Robustness to different lighting conditions
  - Mobile or embedded deployment

---

## Author

Sabhavath Yashwanth  
B.Tech + M.Tech Dual Degree  
IIIT Gwalior
