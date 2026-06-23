# NumberPlate_project

A Python implementation of vehicle number plate detection using the **Haar Cascade** algorithm in OpenCV. Built as a 2nd-year engineering project, this repo detects license/number plates in vehicle images and logs the cropped plate images along with detection data.

## Overview

The project uses a pre-trained Haar Cascade classifier to locate number plates within an input image or video frame. Once a plate region is detected, it is cropped, saved, and logged for further processing (e.g. OCR, record-keeping).

## Project Structure

```
NumberPlate_project/
├── Scripts/             # Core Python scripts for detection
├── model/                # Haar Cascade classifier (.xml) file(s)
├── plates/               # Output folder for cropped/detected plate images
├── number_plates.xlsx    # Log of detected plates (e.g. image name, timestamp)
├── requirements.txt      # Python dependencies
└── README.md
```

## How It Works

1. An input image or video frame is loaded.
2. The frame is converted to grayscale (Haar Cascades work on grayscale intensity gradients).
3. The pre-trained Haar Cascade classifier (stored in `model/`) scans the frame for plate-like rectangular regions.
4. Detected regions are cropped and saved to the `plates/` folder.
5. Metadata about each detection is recorded in `number_plates.xlsx`.

## Requirements

Install dependencies with:

```bash
pip install -r requirements.txt
```

Typical dependencies for this kind of project include:
- `opencv-python`
- `numpy`
- `openpyxl` / `pandas` (for writing to the Excel log)

> Check `requirements.txt` for the exact pinned versions used in this project.

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/ilovevampire/NumberPlate_project.git
   cd NumberPlate_project
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the detection script (from the `Scripts/` folder):
   ```bash
   python Scripts/<script_name>.py
   ```

4. Detected plates will be saved in the `plates/` directory, and detection records will be appended to `number_plates.xlsx`.

> Replace `<script_name>.py` with the actual entry-point script inside the `Scripts/` folder.

## Model

The `model/` directory contains the Haar Cascade XML file used for plate detection (e.g. `haarcascade_russian_plate_number.xml` or a custom-trained cascade). Haar Cascades are lightweight, fast object detectors well-suited for real-time or low-resource applications like this one, though they are less robust than modern deep learning detectors (e.g. YOLO) under varying lighting, angles, or plate formats.

## Output

- **`plates/`** — cropped images of each detected number plate.
- **`number_plates.xlsx`** — a spreadsheet log of detections (filenames, counts, and/or timestamps depending on script implementation).

## Future Improvements

- Integrate OCR (e.g. Tesseract or EasyOCR) to read the actual plate text rather than just detecting the region.
- Replace the Haar Cascade with a deep learning-based detector (YOLOv8/SSD) for improved accuracy across angles, lighting, and plate styles.
- Add support for real-time detection via webcam/video stream.

## Author

[ilovevampire](https://github.com/ilovevampire)

## License

No license specified. Feel free to reach out to the author regarding usage and reuse.
