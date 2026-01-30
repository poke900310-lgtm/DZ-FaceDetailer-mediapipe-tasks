# DZ FaceDetailer

All credits go to https://github.com/nicofdga

## Custom Node for ComfyUI (Stable Diffusion)

DZ FaceDetailer is a custom node for the "ComfyUI" framework inspired by !After Detailer extension from auto1111, it allows you to detect faces using Mediapipe and YOLOv8n to create masks for the detected faces. This custom node enables you to generate new faces, replace faces, and perform other face manipulation tasks using Stable Diffusion AI.

![image](https://github.com/daxthin/facedetailer/assets/78769008/22caf9e4-a29d-4e7c-b6d2-f02679b0dfff)
![image](https://github.com/daxthin/facedetailer/assets/78769008/b7bfa925-c127-427d-9ade-741ddf278648)


### Table of Contents

- [Features](#features)
- [Installation](#installation)

## Features

- Face detection using Mediapipe.
- Multiple face detection support on both models
- Face mask generation for detected faces.
- Latent/sample mapping to generated masks for face manipulation.
- Generate new faces using Stable Diffusion.
- Replace faces using LoRa or embeddings etc.
- batch images support

## Installation
clone the repo [https://github.com/daxthin/DZ-FaceDetailer.git](https://github.com/daxthin/DZ-FaceDetailer.git) in custom_nodes folder

## Maintenance note

This repository includes a **compatibility and maintenance update only**.

- All original functionality, design, and implementation belong to the original author.
- No ownership or authorship is claimed over the original work.

### Summary of maintenance update

This update migrates DZ-FaceDetailer from the deprecated `mediapipe.solutions`
FaceMesh API to **MediaPipe Tasks FaceLandmarker**.

### Why this change was needed

- `mediapipe.solutions` is deprecated
- The legacy FaceMesh API breaks on **Python 3.12**
- MediaPipe Tasks is the officially supported replacement

### What changed

- Replaced legacy FaceMesh with MediaPipe Tasks FaceLandmarker
- Added lazy initialization to avoid ComfyUI startup crashes
- Updated image container usage for newer MediaPipe versions
- Preserved original behavior (YOLO-based detection + convex hull face masks)

### Notes

- Requires an external MediaPipe model file: `face_landmarker.task`
- Download:
  https://storage.googleapis.com/mediapipe-models/face_landmarker/face_landmarker/float16/latest/face_landmarker.task
- The model file is intentionally **not included** in this repository

### Tested on

- ComfyUI v0.11.x
- Python 3.12
