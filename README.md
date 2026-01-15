# Project G.A.N.I. (Ground-Air Navigation Interface)

> Passive reconnaissance and autonomous localization for signal-jammed environments.

Project G.A.N.I. is a dual-agent simulation (UAV + UGV) designed to solve the problem of navigation in GPS-denied zones (forests, deep mines, electronic warfare environments).

Unlike traditional drones that rely on satellite positioning, this system uses **Visual Odometry** and Collaborative **SLAM** (Simultaneous Localization and Mapping) to navigate via onboard camera feeds alone, ensuring **radio silent** stealth capabilities for intelligence gathering.

## 🏗️ System Architecture

This project implements a **Hardware-in-the-Loop** (HIL) simulation architecture:

- **The World (Godot 4):** A 3D physics environment utilizing **digital twin** satellite data (e.g., Jos Plateau, Nigeria) to simulate real-world terrain challenges.

- **The Brain (Python 3):** An external flight controller running Computer Vision algorithms.

- **The Bridge (UDP):** A low-latency socket protocol that transmits video frames and receives velocity commands in real-time.

```{mermaid}
graph LR
    A[Godot Simulation] -- Video Feed (UDP) --> B(Python CV Core)
    B -- Velocity Commands (UDP) --> A
    B -- Map Data --> C[Mission Dashboard]
```

## 🎯 Key Capabilities

- **🚫 GPS-Denied Navigation:** Autonomous station-keeping and return-to-home functionality using Optical Flow and Feature Tracking.

- **🤝 Collaborative Recon:** A heterogeneous team where the **UAV (Aerial Scout)** provides broad mapping while the **UGV (Ground Unit)** inspects under-canopy or obscured targets.

- **🌍 Digital Twinning:** Simulation environments generated from raw satellite elevation data to test algorithms against realistic topography.

- **📡 Resilient Comms Simulation:** Simulates signal degradation and data-mule behavior (store-and-carry) for operations in high-interference zones.

## 🎓 Academic Context

This project serves as the assignment submission for the **Artificial Intelligence for Computer Vision** (ITNPAI2) module at the University of Stirling.

## ⚖️ License & Data Usage

- **Source Code:** The software (GDScript, Python) is open-source and licensed under the **MIT License**. See `LICENSE` for details.

- **Data Disclaimer:** Terrain data, height maps, and satellite imagery included in this repository are for educational and non-commercial demonstration purposes only. They may contain data derived from third-party providers (e.g., Google Earth, NASA) and are subject to their respective Terms of Service. These assets are not covered by the MIT License.
