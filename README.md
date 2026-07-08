# Hand Gesture Recognition System

A real-time hand gesture recognition system using MediaPipe and Keras that can recognize sign language gestures (Hello, Thank You, Yes) through a webcam.

## Features

- **Real-time Hand Detection**: Uses MediaPipe's HandLandmarker for accurate hand pose detection
- **Gesture Classification**: Trained Keras model to recognize specific hand gestures
- **Data Collection**: Built-in data collection script for training new gestures
- **Webcam Integration**: Live video feed processing using OpenCV

## Supported Gestures

- **Hello**: Wave gesture
- **Thank You**: Thank you gestureA
- **Yes**: Affirmative gesture

## Project Structure

```
sign-gesture/
├── datacollection.py          # Script for collecting training data
├── text.py                     # Main prediction script
├── hand_landmarker.task       # MediaPipe hand landmarker model
├── Data/                       # Training data directory
│   ├── Hello/                  # Hello gesture samples
│   ├── Thankyou/               # Thank you gesture samples
│   └── Yes/                    # Yes gesture samples
├── myenv/                      # Python virtual environment
└── README.md                   # This file
```

## Prerequisites

- Python 3.8+
- Webcam

## Installation

1. **Clone or download this project**

2. **Create and activate the virtual environment** (if not already done):
   ```bash
   python -m venv myenv
   # On Windows
   myenv\Scripts\activate
   # On macOS/Linux
   source myenv/bin/activate
   ```

3. **Install dependencies**:
   ```bash
   pip install opencv-python cvzone mediapipe numpy keras
   ```

## Usage

### 1. Collecting Training Data

Run the data collection script to capture hand gesture samples:

```bash
python datacollection.py
```

**Instructions**:
- Edit the `folder` variable in the script to specify which gesture folder to save to (e.g., `Data\Hello`)
- Point your hand at the webcam
- Press 's' to capture images of the gesture
- Press 'q' to quit

**Note**: Ensure you have a trained Keras model files before running the prediction script:
- `keras_model.h5` - The trained model
- `labels.txt` - The class labels

### 2. Running Gesture Recognition

Run the main prediction script:

```bash
python text.py
```

**Instructions**:
- Point your hand at the webcam
- The system will display the recognized gesture in real-time
- Press 'q' to quit

## How It Works

1. **Hand Detection**: MediaPipe's HandLandmarker detects hand position and landmarks
2. **Image Processing**: The detected hand region is cropped and resized to 300x300 pixels
3. **Gesture Classification**: The Keras model predicts which gesture is being made
4. **Display**: The prediction is printed to the console and can be displayed on the video feed

## Model Training

To train a new model:

1. Collect sufficient training data using `datacollection.py` for each gesture
2. Use a separate training script (not included) to train the Keras model
3. Save the model as `keras_model.h5` and labels as `labels.txt`
4. Update the paths in `text.py` to point to your trained model

## Dependencies

- **opencv-python**: Computer vision library for video processing
- **cvzone**: Hand tracking and classification module wrapper
- **mediapipe**: Google's media processing framework for hand detection
- **numpy**: Numerical computing library
- **keras**: Deep learning framework for the classification model

## Troubleshooting

- **Webcam not detected**: Check if another application is using the webcam
- **Hand not detected**: Ensure good lighting and that your hand is visible in the frame
- **Model not found**: Verify that `keras_model.h5` and `labels.txt` are in the correct paths specified in `text.py`

## Future Enhancements

- Support for more gestures
- Real-time display of predictions on video feed
- Confidence score display
- Recording output video
- Multi-hand detection and recognition

## License

This project is open source and available for personal and educational use.

## Author

Created as a hand gesture recognition system for sign language recognition.
