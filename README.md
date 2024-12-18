# JetBot Line Tracking and Obstacle Avoidance

## Overview
This project utilizes the JetBot platform to perform line tracking and obstacle avoidance using real-time image processing and motor control. The bot follows a predefined line while detecting and avoiding obstacles in its path.

## Features
- **Line Tracking**: Uses HSV color space to identify and follow a specific line.
- **Obstacle Detection**: Detects obstacles based on HSV values and calculates their position relative to the robot.
- **Avoidance Strategy**: Implements a timed movement sequence to bypass detected obstacles.
- **Dynamic Widgets**: Provides real-time feedback on the bot's status and environment via interactive widgets.
- **Search and Re-Track**: Automatically searches for the line if tracking is lost.

## Requirements
### Hardware
- JetBot with NVIDIA Jetson Nano
- Camera module compatible with JetBot
- Motor drivers and wheels

### Software
- Python 3.6+
- Libraries:
  - `jetbot`
  - `opencv-python`
  - `numpy`
  - `ipywidgets`
  - `traitlets`
  - `time`

## Installation
1. Clone this repository:
    ```bash
    git clone <repository-url>
    cd <repository-name>
    ```
2. Install required Python libraries:
    ```bash
    pip install -r requirements.txt
    ```
3. Connect the JetBot camera and ensure it is operational.
4. Run the Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

## How It Works
### Line Tracking
- **Color Detection**: The bot uses sliders to set the HSV range for detecting the line.
- **Centroid Calculation**: The line's centroid is calculated to guide the bot's movement.

### Obstacle Detection
- **Red Object Detection**: The bot identifies obstacles based on preconfigured HSV ranges for the color red.
- **Region of Interest (ROI)**: Three ROIs (left, center, right) are defined to determine the obstacle's relative position.

### Control Logic
- **Tracking State**: The bot adjusts its wheel speeds based on the line's position.
- **Avoidance State**: The bot executes a predefined sequence to bypass obstacles.
- **Searching State**: If the line is lost, the bot rotates to locate it again.

## Usage
1. **Run the Jupyter Notebook**:
    - Execute the cells to initialize the camera, robot, and control logic.
    - Adjust the HSV sliders for line and obstacle detection based on the environment.
2. **Enable Tracking**:
    - Toggle the `Enable Tracking` button to start the bot.
3. **Monitor Feedback**:
    - Observe the real-time status updates and visual outputs in the Jupyter Notebook.

## Code Structure
- **Line Tracking**:
  - Detects the line's centroid using HSV masking and contour detection.
  - Adjusts motor speeds based on the centroid's position relative to the camera's center.
- **Obstacle Detection**:
  - Identifies red objects within specific ROIs.
  - Switches to the avoidance state when obstacles are detected.
- **State Machine**:
  - `tracking`: Follows the line.
  - `avoiding`: Executes obstacle avoidance logic.
  - `searching`: Rotates to locate the line if tracking is lost.

## Widgets
- **HSV Range Sliders**:
  - Adjust the HSV thresholds for line and obstacle detection.
- **Image Widgets**:
  - Display the processed images for line and obstacle detection.
- **Status Indicators**:
  - Show the current bot state, motor speeds, and obstacle status.

## Troubleshooting
- **Line Not Detected**:
  - Adjust the HSV range sliders until the line is highlighted in the mask image.
- **Obstacle Detection Issues**:
  - Ensure the HSV range for obstacles matches the environment.
- **Performance Issues**:
  - Reduce the camera resolution or processing frequency.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgments
- NVIDIA for the JetBot platform
- OpenCV and Python communities for extensive resources

