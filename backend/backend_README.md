# ☁️ Backend Processing Pipeline (Google Colab)

# Overview

This folder contains the student-developed backend workflow for the **3D Gaussian Splat Tour Camera App**.

The backend is implemented as a **Google Colab notebook** that runs on a Colab NVIDIA GPU. It receives uploaded image/video data from the mobile app, processes the input through a reconstruction pipeline, and produces files that can be viewed in a 3D splat viewer.

---

# 🧠 What the Backend Does

```text
Receive Photos / Videos
        ↓
Prepare Input Files
        ↓
Run COLMAP Structure-from-Motion
        ↓
Train 3D Gaussian Splatting Model
        ↓
Export .splat / .ply Outputs
        ↓
Serve Viewer URL Back to App
```

At a high level, the backend:

- Receives photos and videos from the mobile app
- Organizes uploaded data into processing folders
- Uses COLMAP for structure-from-motion
- Uses a Gaussian Splatting training pipeline to generate 3D outputs
- Exports viewable reconstruction files
- Hosts/serves a viewer URL that the app can open

---

# 📂 Colab Notebook Layout

The notebook is organized into sections that should be run from top to bottom.

---

## 1️⃣ Verify GPU

The notebook first checks that the Colab runtime has GPU access.

Tools used:

- `nvidia-smi`
- `torch`
- CUDA GPU runtime

Purpose:

- Confirms GPU availability
- Prints the detected GPU name and memory
- Stops early if no GPU is available

---

## 2️⃣ Mount Google Drive Cache

The notebook mounts Google Drive to store build caches.

Tools used:

- `google.colab.drive`
- Python `os`
- Python `subprocess`
- Google Drive

Purpose:

- Saves built dependencies so future runs are faster
- Stores cached COLMAP and LichtFeld-Studio build files
- Avoids rebuilding large tools every time the notebook runs

---

## 3️⃣ Install System Dependencies

The notebook installs Linux system packages needed for reconstruction and building from source.

Tools/libraries used include:

- `apt-get`
- `cmake`
- `ninja-build`
- `build-essential`
- `libboost`
- `libeigen3`
- `libflann`
- `libfreeimage`
- `libmetis`
- `libgoogle-glog`
- `libgflags`
- `libsqlite3`
- `libglew`
- `libglvnd`
- `libcgal`
- `libceres`
- `imagemagick`

Purpose:

- Prepares the Colab machine for computer vision and 3D reconstruction tools
- Provides required libraries for COLMAP and Gaussian Splatting builds

---

## 4️⃣ Build COLMAP

The notebook builds **COLMAP** from source with CUDA support.

Tool used:

- [COLMAP](https://github.com/colmap/colmap)

Purpose:

- Runs structure-from-motion
- Extracts image features
- Matches images
- Estimates camera poses
- Produces reconstruction data needed for the Gaussian Splatting stage

---

## 5️⃣ Build Gaussian Splatting Engine

The notebook builds a 3D Gaussian Splatting engine from source.

Tool used:

- [LichtFeld-Studio](https://github.com/MrNeRF/LichtFeld-Studio)

Build tools used:

- `gcc-14`
- `g++-14`
- `cmake`
- `ninja`
- `vcpkg`
- CUDA
- C++ build tools

Purpose:

- Trains the 3D Gaussian Splatting reconstruction
- Generates output files that can be converted into viewable formats

---

## 6️⃣ Install Python Packages

The notebook installs Python packages used for the API server, file handling, image processing, and cloud upload.

Python libraries used:

- `fastapi`
- `uvicorn[standard]`
- `python-multipart`
- `opencv-python-headless`
- `pillow-heif`
- `rawpy`
- `plyfile`
- `numpy`
- `aiofiles`
- `boto3`
- `torch`

Purpose:

- Runs the backend API server
- Handles uploaded files
- Processes images and video frames
- Reads RAW/HEIF image formats
- Works with reconstruction output files
- Supports cloud/object-storage upload when configured

---

## 7️⃣ Install Cloudflare Tunnel

The notebook installs and runs Cloudflare Tunnel.

Tool used:

- `cloudflared`

Purpose:

- Exposes the Colab FastAPI server through a public URL
- Allows the mobile app to communicate with the backend while it runs in Colab

> Private tunnel tokens should be stored securely in Colab Secrets and should never be committed to GitHub.

---

## 8️⃣ Install Splat Transform Tool

The notebook installs PlayCanvas' splat conversion tool.

Tool used:

- `@playcanvas/splat-transform`

Purpose:

- Converts generated `.splat` files into web-viewable formats
- Helps prepare reconstruction output for browser-based viewing

---

## 9️⃣ Backend API Server

The notebook runs a FastAPI server inside Colab.

Tools/libraries used:

- `FastAPI`
- `Uvicorn`
- `python-multipart`
- `aiofiles`
- Python `subprocess`
- Python `pathlib`
- Python `zipfile`
- Python `json`
- Python `uuid`

Purpose:

- Receives uploads from the app
- Starts processing jobs
- Tracks job status
- Stores job metadata
- Returns result links or viewer URLs

---

## 🔟 Local Manual Pipeline

The notebook also supports manually uploading a zip file directly into Colab.

Tools/libraries used:

- Python `glob`
- Python `zipfile`
- Python `shutil`
- Python `subprocess`
- Python `struct`
- `cv2`
- `numpy`

Purpose:

- Allows testing the backend without using the mobile app
- Processes a local `.zip` of images/videos directly in Colab
- Useful for debugging and demonstration

---

# 🛠 Specific Tools and Libraries Used

## Backend / Colab

- Google Colab
- NVIDIA GPU runtime
- CUDA
- Google Drive mounted cache
- Colab Secrets

## Reconstruction

- COLMAP
- LichtFeld-Studio
- 3D Gaussian Splatting
- PlayCanvas SuperSplat
- PlayCanvas `splat-transform`

## API / Server

- FastAPI
- Uvicorn
- Cloudflare Tunnel / `cloudflared`

## Python Libraries

- `torch`
- `opencv-python-headless`
- `numpy`
- `rawpy`
- `pillow-heif`
- `plyfile`
- `aiofiles`
- `python-multipart`
- `boto3`

## Build / System Tools

- `apt-get`
- `cmake`
- `ninja-build`
- `build-essential`
- `gcc-14`
- `g++-14`
- `vcpkg`
- `curl`
- `zip`
- `unzip`
- `tar`
- `pkg-config`
- `imagemagick`

---

# 🔐 Public Repository Notes

This backend folder intentionally excludes:

- API keys
- Cloudflare tunnel tokens
- R2/cloud storage credentials