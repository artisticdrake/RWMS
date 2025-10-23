---
Title: "Rainwater Management System using Raspberry Pi & OCR-Based Water Level Detection"
Author: "Preetham Prathipati"
---

# 🌧️ Rainwater Management System using Raspberry Pi & OCR-Based Water Level Detection

This project presents an **automated rainwater monitoring and alert system** built on a **Raspberry Pi**, leveraging **computer vision** and **optical character recognition (OCR)** to measure water levels in real time.  
It captures a live RTSP feed from a CCTV camera, processes each frame to detect the water level on a physical scale inside a sealed chamber, and sends **email alerts** when thresholds are exceeded.

**Impact:** Deployed across campus, this system improved flood response time by nearly **30%** through autonomous monitoring.

---

# Workflow Summary

1. **Live Feed Input**
   - Receives RTSP input from a CCTV camera.
   - Pi auto-launches the script at OS boot.

2. **Image Preprocessing**
   - Converts frames to grayscale.
   - Detects edges via Canny and line detection.
   - Applies **Hough Transform** for line detection.

3. **Measurement Box**
   - Metal box contains water and a measurement scale.
   - Defines region of interest for analysis.

4. **OCR Level Detection**
   - Performs **Tesseract OCR** on detected region.
   - Dynamically adjusts the OCR window based on edge position.

5. **Threshold Alert**
   - If detected level ≥ threshold → sends SMTP email alert.
   - Logs value and prints alert on console.

6. **Autonomous Operation**
   - Script runs at system startup using `bootsh` script.
   - Pi powers off and restarts periodically to log water levels.

---

# Tech Stack

| **Component**         | **Description**                                                                 |
|------------------------|---------------------------------------------------------------------------------|
| **Hardware**           | Raspberry Pi 4, CCTV camera (RTSP), metal box with scale                       |
| **Languages**          | Python                                                                         |
| **Libraries**          | OpenCV, NumPy, pytesseract, smtplib, os, time                                  |
| **Tools / Methods**    | Hough Transform, Edge Detection, Grayscale Filtering, OCR                       |
| **OS Configuration**   | Auto-run via `rc.local` / `systemd`, periodic restart cycle                    |

# Glossary

| **Term** | **Definition** |
|-----------|----------------|
| **Raspberry Pi** | A small single-board computer used here as the core controller for processing and automation. |
| **RTSP (Real Time Streaming Protocol)** | A network protocol used for streaming video from CCTV cameras to the Raspberry Pi in real time. |
| **Grayscale Conversion** | Image processing technique that removes color information, reducing an image to intensity shades for easier edge detection. |
| **Edge Detection** | A method to identify object boundaries within an image; typically implemented using algorithms like the Canny detector. |
| **Hough Transform** | A mathematical method used to detect geometric shapes like lines in images. It’s applied here to identify the scale’s edges. |
| **OCR (Optical Character Recognition)** | Technology that converts images of text (like numbers on a water scale) into machine-readable text, used via Tesseract. |
| **Tesseract OCR** | An open-source OCR engine developed by Google, used to detect and extract text from images. |
| **SMTP (Simple Mail Transfer Protocol)** | Standard protocol for sending emails; used by the Raspberry Pi to send automated alert messages. |
| **Threshold Level** | A pre-defined limit of water level at which the system triggers an alert. |
| **Systemd / rc.local** | Linux startup services used to automatically launch the Python script at OS boot. |
| **OpenCV** | A popular open-source library for real-time computer vision tasks such as image preprocessing and edge detection. |
| **NumPy** | A Python library used for numerical operations, often for handling matrices and pixel-level data. |
| **pytesseract** | Python wrapper for Tesseract OCR, enabling easy text extraction from images. |
| **smtplib** | Python’s built-in library for sending emails through the SMTP protocol. |
| **Canny Edge Detection** | A multi-stage edge detection algorithm that provides clean edge maps for further analysis. |
| **Region of Interest (ROI)** | The specific window or sub-region of the image that the system focuses on for water level detection. |
| **Auto-Run Configuration** | A setup where the script executes automatically every time the OS boots, ensuring continuous operation. |
| **Periodic Restart** | The Raspberry Pi periodically powers off and restarts to record fresh water-level data, ensuring reliability. |
| **Flood Response Time** | The duration between a flood-triggering event and the system or personnel responding to it — reduced by 30% with this project. |


