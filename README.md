# Fatigue Checker

Fatigue Guard is an ultra-lightweight, AI-driven background service designed to silently monitor your face and trigger native Windows alerts when you exhibit strong symptoms of drowsiness or micro-sleeps. 

It was built using the UTARLDD dataset and uses MediaPipe alongside a Bidirectional PyTorch LSTM.

## How It Works
Rather than analyzing entire chunky video frames (which destroys laptop battery life), Fatigue Guard efficiently extracts exactly `6` tiny mathematical values from your face 10 times a second:
- Left Eye Aspect Ratio (EAR)
- Right Eye Aspect Ratio
- Mouth Aspect Ratio (MAR)
- Mouth over Eye Ratio (MOE)
- Head Pitch
- Head Yaw

These values are converted into *Velocity Tensors* (Δ) dynamically. A PyTorch LSTM network then reads a sliding 10-second window of your facial velocities to flag potential moments of sleepiness. 

To eliminate false-positives (like looking at your phone), the output predictions are constrained mathematically by a heavy **Exponential Moving Average**. You must exhibit sustained Drowsy behavior to trigger an alarm.

## Installation
Go to releases and download the latest zip file. Extract the zip file. 

## Running the App
To start the background service, run the exe file in the extracted zip file.
This will launch the app completely invisibly in your Windows background. A small blue "eye" icon will appear in your System Tray (hidden icons in the bottom right corner of your taskbar).

**To configure settings:**
1. Right-click the blue eye icon in the system tray
2. Click **Open GUI**
3. Select your exact hardware camera from the dropdown menu, preview the live feed, or cleanly terminate the background service.

