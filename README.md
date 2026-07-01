# Real-time Bottle Defect Detection

This is a Python script that checks bottles for defects on a production line using webcams. It uses an AI model (YOLOv4) to check the bottle shape, and regular image processing (OpenCV) to check the cap and liquid level.

## How it works
The program uses 3 cameras and runs them on separate processes so the interface doesn't lag:
* **Camera 0 & 1:** Look at the bottle from two angles and use YOLOv4 (with CUDA/GPU acceleration) to check for shape issues.
* **Camera 2:** Looks at the top of the bottle to check if the cap is missing/crooked and if the liquid is underfilled or overfilled.
* **GUI:** Built with Tkinter to show all three camera feeds and output the status (Good/Defect).

## Requirements
* Python 3
* OpenCV (needs to be built with CUDA support for the AI model to run fast)
* NumPy
* Pillow (for displaying images in Tkinter)
* Linux OS (the camera setup uses `V4L2`)

## Files needed in the folder
You need to put your trained YOLO model files in the same directory:
* `yolov4-custom.cfg`
* `yolov4-custom_last_version6.weights`
* `yolo.names`

## How to run
1. Plug in your 3 USB webcams. 
2. Double-check the camera IDs in the code (`setup_cam_shape(0)`, `setup_cam_shape(1)`, and `setup_cam_cap_and_fill(2)`) match your cameras.
3. Run the script:
   ```bash
   python main.py

