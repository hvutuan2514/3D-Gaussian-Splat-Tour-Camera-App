# 📸 3D Gaussian Splat Tour Camera App

<div align="center">

### Mobile Capture → Cloud Processing → Reconstruction → Interactive Viewing

A student-developed image capture and reconstruction workflow designed to simplify the process of collecting images, processing them in the cloud, and visualizing reconstructed outputs.

---

![Platform](https://img.shields.io/badge/Platform-iOS%20%2B%20Android-blue)
![Status](https://img.shields.io/badge/Status-Finished-green)
![Focus](https://img.shields.io/badge/Focus-Image%20Reconstruction-orange)

</div>

---

# 🚀 Project Overview

This project is a mobile-based camera and reconstruction system that allows users to:

- Capture images directly from a mobile application
- Upload data to cloud/backend services
- Process captured images through reconstruction pipelines
- View generated outputs in an interactive interface

The goal of the project is to create a streamlined workflow that combines image capture, cloud processing, and visualization into a single user experience.

This repository intentionally shares only the public-facing architecture and workflow of the project while excluding confidential sponsor/company implementation details.

---

# ❗ Problem the Project Solves

Traditional image reconstruction workflows can be difficult because they often require users to:

- Manually transfer image files
- Use multiple disconnected tools
- Configure processing pipelines separately
- Wait for reconstruction results without integrated feedback
- View outputs in external software

This project simplifies the workflow by integrating the major steps into one connected system.

---

# 🧠 High-Level System Architecture

```text
Mobile Camera App
        ↓
Image Upload / Cloud Storage
        ↓
Backend Processing Pipeline
        ↓
Reconstruction Generation
        ↓
Interactive Viewing Interface
```

---

# 🔄 Main Workflow

## 1️⃣ Capture Images
Users capture multiple images using the mobile application camera interface.

## 2️⃣ Upload to Backend / Cloud
The captured image set is uploaded for processing and storage.

## 3️⃣ Reconstruction Processing
Backend services process the uploaded images and generate reconstruction outputs.

## 4️⃣ View Results
The generated results are displayed through the application's viewing interface.

---

# 🛠 Technologies & Tools

This project uses a combination of mobile development, cloud communication, and image-processing technologies.

Examples of technologies involved include:

- Mobile application frameworks
- Camera APIs
- Cloud storage/backend services
- Image processing pipelines
- Reconstruction workflows
- REST API communication
- UI/UX mobile design tools

---

# 📷 Screenshots

---

## 🏠 Home Screen

![Home Screen](./screenshots/home-screen.png)

*Main landing page of the application.*

---

## 📸 Camera Capture Interface

![Capture Screen](./screenshots/capture-screen.png)

*Users capture image sets directly from the app.*

---

## ☁️ Upload & Processing

![Processing Screen](./screenshots/processing-screen.png)

*Images are uploaded and processed through backend services.*

---

## 🧩 Reconstruction Viewer

![Viewer Screen](./screenshots/viewer-screen.png)

*Generated reconstruction results displayed inside the application.*

---

# ⚠️ Current Limitations

Because the project is still evolving, some limitations may include:

- Processing time depending on image count
- Reconstruction quality variability
- Network dependency for uploads
- Device compatibility differences
- Limited real-time feedback during processing

---

# 🔮 Future Improvements

Potential future enhancements include:

- Faster cloud processing
- Improved reconstruction accuracy
- Better visualization tools
- Real-time progress feedback
- Enhanced offline support
- Expanded device compatibility
- Improved error handling and recovery

---

# 🔐 Public Repository Notes

This repository intentionally excludes:

- Private API keys
- Sponsor-owned systems
- Internal infrastructure
- Sensitive implementation details

The goal of this public repository is to explain the project idea, workflow, and architecture at a high level while protecting confidential information.

---
