# Parking Space Counter

A computer vision project that detects and counts available parking spaces in real-time using Python and OpenCV. This system utilizes image processing techniques to distinguish between empty and occupied parking spots based on a video feed.

## 📂 Project Structure

* **`ParkingSpacePicker.py`**: A utility script to manually select and define parking spot coordinates on a reference image.
* **`main.py`**: The core application that processes the video feed, applies image thresholds, and counts available spaces.
* **`CarParkPos`**: A pickle file capable of storing the coordinates of the selected parking spaces.

## 🚀 Features

* **Manual Position Selector**: users can define parking spots by clicking on an image. Left-click adds a spot, and right-click removes it.
* **Real-Time Detection**: Monitors a video feed (`carPark.mp4`) to track parking availability continuously.
* **Dynamic Status Display**:
    * **Green**: Indicates an empty parking spot.
    * **Red**: Indicates an occupied parking spot.
* **Live Counter**: Displays the total count of free spaces versus the total number of defined spaces using `cvzone`.

## 🛠️ Dependencies

Ensure you have the following Python libraries installed:

* `opencv-python`
* `cvzone`
* `numpy`
* `pickle` (Standard Python library)

## ⚙️ How It Works

### 1. Position Selection (`ParkingSpacePicker.py`)
This script opens a reference image (`carParkImg.png`). It detects mouse events to record the top-left coordinates of parking spots. These coordinates are saved into a `CarParkPos` file using the `pickle` module for the main script to access.

### 2. Processing Pipeline (`main.py`)
The main script processes the video feed through several stages to isolate vehicles:
1.  **Grayscale & Blur**: Converts the image to grayscale and applies a Gaussian blur.
2.  **Adaptive Thresholding**: Converts the image to a binary format (black and white) to highlight structure.
3.  **Median Blur & Dilation**: Removes noise and thickens the pixel edges for better detection.
4.  **Pixel Counting**: The script crops the region of every defined parking spot and counts the non-zero (white) pixels.
    * If the pixel count is **< 900**, the spot is considered **free**.
    * If the pixel count is **> 900**, the spot is considered **occupied**.

## 📝 Usage

1.  **Define Spots**:
    Run the picker script to define your parking layout.
    ```bash
    python ParkingSpacePicker.py
    ```
    * **Left-click** to add a parking box.
    * **Right-click** to remove a parking box.

2.  **Run Detection**:
    Start the detection system.
    ```bash
    python main.py
    ```

> **Note**: You may need to update the file paths for the video source and `CarParkPos` file in `main.py` to match your local directory structure.
