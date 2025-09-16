# Voice-Controlled Toy Car with Deep Learning

A smart toy car system that responds to voice commands using LSTM-based deep learning. The system processes voice input, classifies commands using a neural network, and controls DC motors accordingly.

## Features

- Voice command recognition for 5 actions: forward, backward, left, right, and stop
- LSTM-based deep learning model with over 90% accuracy
- Real-time audio processing using MFCC features
- Arduino-based motor control system
- Complete integration from voice input to physical movement

## System Architecture

1. **Voice Input Processing**
    - Records 2-second audio clips at 8000Hz sample rate
    - Converts audio to MFCC features (39 coefficients)
    - Pads input to uniform 25000 samples

2. **Deep Learning Model**
    - LSTM layer with 128 units
    - MaxPooling and Flatten layers
    - Softmax output for 5-class classification

3. **Hardware Control**
    - Arduino-based motor control
    - H-bridge circuit for DC motor direction control
    - Serial communication between Python and Arduino

## Requirements

### Software
- Python 3.x
- TensorFlow/Keras
- librosa
- soundfile
- pyaudio
- python_speech_features
- pyserial
- Arduino IDE

### Hardware
- Arduino board
- DC motors with H-bridge driver
- Microphone
- Power supply
- Chassis and wheels

## File Structure

- `record.py` - Records training audio samples
- `25xpadding.py` - Preprocesses audio files with padding
- `Createmodel.py` - Trains the LSTM model
- `Speak.py` - Real-time voice command processing
- `toycar.ino` - Arduino motor control code

## Setup and Usage

1. Connect the Arduino circuit according to the pin configuration in `toycar.ino`
2. Upload the Arduino code to the board
3. Install Python dependencies: `pip install tensorflow keras librosa soundfile pyaudio python_speech_features pyserial`
4. Run `Speak.py` for real-time voice control

## Model Training

The model was trained on 2000 samples per command class using:
- MFCC features with 39 coefficients
- LSTM architecture
- Categorical cross-entropy loss
- RMSprop optimizer