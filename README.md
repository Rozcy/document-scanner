# Document Scanner

Document Scanner is a powerful Python-based application that utilizes the OpenCV library to transform regular images of documents into clean, digital scans. It leverages advanced computer vision techniques to detect the edges of the document, find its contours, apply perspective correction, and enhance the visual quality of the scanned document.

## Features

- **Automatic Document Detection**: The application can accurately detect the boundaries of the document within an image, even in the presence of background clutter or skewed perspectives.

- **Perspective Correction**: By finding the four corner points of the document, the application applies a perspective transform to obtain a top-down, distortion-free view of the document.

- **Image Enhancement**: The scanned document is processed to improve its visual quality, including thresholding and binarization, resulting in a clear, high-contrast image suitable for further processing or archiving.

- **Command-Line Interface**: The application can be run from the command line, making it easy to integrate into automated workflows or batch processing pipelines.

## Requirements

- Python 3.x
- OpenCV
- NumPy
- Imutils
- scikit-image

## Installation

1. Clone the repository:
  ```sh
git clone https://github.com/YegorCherov/document-scanner.git
```

2. Install the required packages:
  ```sh
pip install -r requirements.txt
  ```
## Usage

1. Navigate to the project directory:
  ```sh
cd document-scanner
  ```
2. Run the scanner script with the path to your image:
  ```sh
python scanner.py --image /path/to/your/image.jpg
  ```
The script will process the image, apply the document scanning steps, and display the original and scanned images.

## Code Explanation

The application follows these main steps:

1. **Detect edges of the document using edge detection**
  - The image is converted to grayscale and blurred to reduce noise.
  - The Canny edge detection algorithm is applied to find the edges of the document within the image.

2. **Find the contour representing the document**
  - The contours of the detected edges are identified.
  - The largest contour, assumed to be the document, is selected and approximated to a quadrilateral shape.

3. **Apply a perspective transform to obtain a top-down view**
  - Using the four corner points of the quadrilateral, a perspective transform is applied to the original image, resulting in a top-down, rectified view of the document.

4. **Threshold the image to enhance the document's appearance**
  - The warped (transformed) image is converted to grayscale and thresholded using a local adaptive thresholding technique.
  - This step enhances the contrast and clarity of the document, making it suitable for further processing or archiving.

The code uses the `cv2` (OpenCV) library for image processing operations, `numpy` for numerical operations, `imutils` for convenient image processing functions, and `skimage` for thresholding the image.

## Demo

![Demo Image](/Images/Demo.png)

The demo image shows the original document image on the left and the scanned, top-down view of the document on the right, demonstratin