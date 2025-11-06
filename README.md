Interactive Image Segmentation with SAM and Gradio

This project is an interactive web application that performs real-time, promptable image segmentation using the Segment Anything Model (SAM). Users can upload an image, click on any object, and instantly receive a segmentation mask and an isolated transparent PNG of that object.

The application is built using the ultralytics library for the SAM model and Gradio for the user interface.

Features

Interactive Point-Based Segmentation: Click on any object to generate a segmentation mask.

Real-Time Inference: Uses the lightweight sam_b.pt model for fast segmentation.

Object Isolation: Automatically generates a transparent PNG of the segmented object, ready for download.

Performance Metrics: Displays the model load time and the inference time for each segmentation.

Simple Web UI: Built with Gradio for easy drag-and-drop/clipboard image uploads.

How It Works: The SAM Architecture

This tool leverages the powerful three-stage architecture of the Segment Anything Model:

Image Encoder: A heavy, pre-trained Vision Transformer (ViT) runs once on the uploaded image to generate detailed, 1-to-1-scale image embeddings. This is the computationally intensive step and is done first.

Prompt Encoder: The user's click (a positive point prompt) is rapidly encoded into a sparse vector embedding. This is extremely fast.

Mask Decoder: A lightweight decoder takes the rich image embeddings and the specific prompt embedding, combining them to predict multiple mask proposals (e.g., whole, part, sub-part) and their confidence scores.

The application then selects and displays the mask with the highest confidence score, all in real-time.

Setup and Installation

The entire application is contained within a single Jupyter Notebook (.ipynb).

Clone or Download: Get the .ipynb file.

Create a Virtual Environment (Recommended):

python -m venv sam_env
source sam_env/bin/activate  # On Linux/macOS
.\sam_env\Scripts\activate  # On Windows


Install Dependencies:
The notebook's first cell installs everything, but you can also install them manually:

pip install ultralytics gradio torch numpy opencv-python-headless


How to Run

Launch Jupyter:
Open the Untitled14.ipynb (or your renamed file) in a Jupyter environment like Jupyter Lab, Jupyter Notebook, or Google Colab.

Run All Cells:
Execute all cells from top to bottom. The script will:

Install dependencies.

Import libraries.

Download and load the sam_b.pt model weights.

Define helper functions for segmentation and image processing.

Launch the Gradio web server.

Open the App:
The last cell will output a local URL (e.g., http://127.0.0.1:7860) and a public Gradio URL (e.g., https://...gradio.live). Click either link to open the interactive app in your browser.

How to Use the App

Upload Image: Use the "1. Upload Image" panel on the left to drag-and-drop, upload, or paste an image from your clipboard.

Click to Segment: The image will appear in the "2. Click on an Object to Segment" panel on the right. Simply click on any object you want to isolate.

View Results:

The right-hand panel will update to show the original image with the segmentation mask overlaid in green.

The "3. Isolated Object (PNG)" panel on the left will show the segmented object on a transparent background.

The "📊 Performance & Stats" box will show the inference time for your click.

Save Output: You can right-click or long-press the "Isolated Object" image to save it as a transparent PNG.
