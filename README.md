🚗 Automated Parking Space Counter
This project uses Computer Vision techniques to detect and count available parking spaces in a video feed. It processes video footage to differentiate between empty and occupied spots based on pixel density, providing a real-time count of free spaces.

🌟 Features
Parking Spot Selector (ParkingSpacePicker.py): A utility tool to manually define parking spots on a reference image using mouse clicks.

Left Click: Add a parking spot.

Right Click: Remove a parking spot.

Persistence: Saves coordinates to a pickle file for the main application to use.

Real-time Detection (main.py): Processes video input to monitor parking status.

Image Processing Pipeline: Utilizes Grayscale, Gaussian Blur, Adaptive Thresholding, Median Blur, and Dilation to isolate vehicles.

Dynamic Counters: Visualizes the number of free spots vs. total spots directly on the video feed.

Color Indicators: Green for available spots, Red for occupied spots.

🛠️ Tech Stack
Python 3.x

OpenCV (cv2): For image processing and video manipulation.

Cvzone: For easy overlay of text and graphics.

NumPy: For matrix operations and kernel definition.

Pickle: For serializing and saving parking space coordinates.

📂 File Structure
ParkingSpacePicker.py: Script to interactively select and save parking spot coordinates.

main.py: Main script that runs the detection algorithm on the video feed.

CarParkPos: (Generated) Pickle file containing the coordinates of selected spots.

carParkImg.png: Reference image used for selecting spots.

carPark.mp4: Source video file for testing the detection system.

⚙️ How It Works
Coordinate Mapping: The user marks the Region of Interest (ROI) for every parking spot using the picker script.

Preprocessing: The video frame is converted to binary (black and white) using adaptive thresholding to highlight edges and objects (cars).

Pixel Counting: The system crops the frame to the defined ROIs and counts the number of non-zero (white) pixels.

Decision Making:

If pixel count < 900 (variable threshold): Spot is Empty.

If pixel count > 900: Spot is Occupied.

🚀 How to Run
Install Dependencies:

Bash

pip install opencv-python cvzone numpy
Select Parking Spots: Run the picker to define the layout.

Bash

python ParkingSpacePicker.py
Click on the image to define spots. Close the window when finished to save.

Run Detection: Run the main script to see the results.

Bash

python main.py
Note: Ensure the file paths in main.py (currently absolute paths like C:\Users\kamal...) are updated to match your local directory structure or changed to relative paths.
