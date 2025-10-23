---
title: "Rainwater Management System using Raspberry Pi & OCR-Based Water Level Detection"
author: "Preetham Prathipati"
date: "`r Sys.Date()`"
output:
  html_document:
    toc: true
    toc_depth: 3
    number_sections: false
  pdf_document:
    toc: true
---

# 🌧️ Overview

This project presents an **automated rainwater monitoring and alert system** built on a **Raspberry Pi**, leveraging **computer vision** and **optical character recognition (OCR)** to measure water levels in real time.  
It captures a live RTSP feed from a CCTV camera, processes each frame to detect the water level on a physical scale inside a sealed chamber, and sends **email alerts** when thresholds are exceeded.

> **Impact:** Deployed across campus, this system improved flood response time by nearly **30%** through autonomous monitoring.

---

# 🧠 Workflow Summary

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
   - Script runs at system startup using `rc.local` or `systemd`.
   - Pi powers off and restarts periodically to log water levels.

---

# 🧩 Tech Stack

```{r, echo=FALSE}
library(knitr)
tech <- data.frame(
  Component = c("Hardware", "Languages", "Libraries", "Tools / Methods", "OS Configuration"),
  Description = c(
    "Raspberry Pi 4, CCTV camera (RTSP), metal box with scale",
    "Python",
    "OpenCV, NumPy, pytesseract, smtplib, os, time",
    "Hough Transform, Edge Detection, Grayscale Filtering, OCR",
    "Auto-run via rc.local / systemd, periodic restart cycle"
  )
)
kable(tech, caption = "Technology Stack", align = "l")
