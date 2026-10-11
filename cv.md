---
layout: default
title: Curriculum Vitae
permalink: /cv/
description: Academic CV of Dr. Muhammad Ibrahim — research scientist, adjunct research fellow at UWA.
---

# Curriculum Vitae

> A PDF version of my CV is available on request via <a href="mailto:ibrahim80876@gmail.com">email</a> or via the <a href="https://github.com/IbrahimUWA" target="_blank" rel="noopener">GitHub repository</a> hosting this site.

## Education

| Degree | Institution | Year |
|---|---|---|
| **PhD, Computer Science** — *3D Scene Understanding from LiDAR Point Clouds*. Coursework: HD. Supervisor: Prof. Ajmal Mian. | **The University of Western Australia** | 2019 – 2023 |
| **MSc, Personal Mobile &amp; Satellite Communication** (Major: Remote Sensing &amp; Communication) | **University of Bradford, UK** | 2009 – 2010 |
| **BSc, Computer Systems Engineering** | University of Engineering &amp; Technology (UET), Pakistan | 2004 – 2008 |

## Current appointments

- **Research Scientist** — Department of Primary Industries and Regional Development (DPIRD), Western Australia. *Sept 2023 – present.*
- **Adjunct Research Fellow** — School of Physics, Mathematics and Computing, **The University of Western Australia**. *June 2024 – May 2027.*
- **Research Assistant (Casual)** — AI &amp; Robotics, **University of Canberra**. *Oct 2025 – present.*

## Previous appointments

- **Research Assistant &amp; Doctorate Researcher**, Computer Science &amp; Software Engineering, UWA — Aug 2019 to Dec 2023.
- **Data Scientist (DARPA project, joint with University of Central Florida)**, UWA — Oct 2020 to Mar 2022.
- **Teaching Assistant**, UWA — 2 years during PhD (Graphics &amp; Animation; Software Engineering with Java).
- **Assistant Professor**, Department of Electrical Engineering, **FAST-NUCES Peshawar, Pakistan** — Feb 2013 to July 2019.

## Selected technical expertise

- **Languages**: Python, R, C, C++, C#, Java, Verilog HDL, Assembly; **Parallel**: CUDA, OpenCL, OpenMP, MPI, Dask, Spark.
- **ML / DL**: PyTorch, TensorFlow, Keras, Scikit-learn, OpenCV, Hugging Face.
- **3D / Geo**: CloudCompare, MeshLab, LAStools, Ouster Studio, ROS, QGIS, Metashape Pro, DJI Terra, WebODM, Google Earth Engine.
- **Cloud / HPC**: Pawsey Setonix supercomputer, Pawsey Acacia object storage, Pawsey Nebula, Microsoft Azure, AWS.
- **Sensors &amp; platforms**: Ouster LiDAR (16/64/128 ch), Honeywell IMU, RTK GNSS, DJI Mavic 3 Multispectral, DJI Matrice 300 / 350 RTK, Phase-One RGB, GOBI and Kelvis RGB + LiDAR + VNIR payloads, Headwall hyperspectral, multispectral, thermal cameras, IoT field sensors, FPGA / DSP kits.
- **Tooling**: Git/GitHub, Linux/Bash, LaTeX, Docker.

## Drone data collection &amp; processing

I plan, fly and process UAV campaigns for DPIRD and the Australian Plant Phenomics Network (APPN) across Western Australian field trials, from flight planning and ground control to calibrated, FAIR-ready data products on Pawsey.

- **DJI Mavic 3 Multispectral** — RGB and multispectral (green, red, red-edge, NIR with sunlight sensor) surveys for vegetation indices, flowering, weed and canopy-cover mapping.
- **DJI Matrice 300 RTK and Matrice 350 RTK** — heavy-lift RTK platforms carrying the **Phase One** high-resolution camera (IIQ raw captures converted to geotagged JPEG / GeoTIFF for Metashape and QGIS) for mm-scale plot imagery.
- **GOBI integrated payload** — co-registered **RGB, LiDAR and VNIR hyperspectral (172 bands)** acquisition in a single flight, with co-aligned GNSS / IMU logging.
- **Kelvis integrated payload** — co-registered **RGB, LiDAR and VNIR** acquisition for structural and spectral phenotyping of the same plots.
- **Processing pipeline**: PPK / RTK trajectory and GNSS file filtering, orthomosaicking and dense reconstruction (Agisoft Metashape, DJI Terra, WebODM), radiometric and reflectance calibration with field spectrometer ground truth (SED to Excel), per-plot extraction from raw frames and orthomosaics (Plot Extractor), LiDAR ground classification and canopy traits, VNIR cube QC and spectral indices (PhenoApp), SAM&nbsp;3.1-assisted labelling (CropLabel), and transfer, sync and publishing of terabyte-scale datasets to Pawsey Acacia (PDMA).
- **Outputs**: plant height, biomass, canopy cover and gap metrics, ~200 spectral indices, weed / crop maps and flowering predictions delivered per plot with QC tables and provenance for agronomists and breeders.

## Citations &amp; impact

A continuously updated list of publications, citations and h-index is on my **[Google Scholar profile]({{ site.google_scholar }})**.

## References

1. **Prof. Ajmal Mian** — School of Computer Science and Software Engineering, UWA. <a href="mailto:ajmal.mian@uwa.edu.au">ajmal.mian@uwa.edu.au</a>. *(PhD Principal Supervisor)*
2. **Assoc. Prof. Hafeez Ur Rehman** — Dean, Dean College of Computing and Data Science, Oryx University with Liverpool John Moores University, Doha  Qatar. <a href="mailto:H.UrRehman@ljmu.ac.uk">H.UrRehman@ljmu.ac.uk</a>. *(Academic Reference)*
3. **Assoc. Prof. Michael Wise** — School of Computer Science and Software Engineering, UWA. <a href="mailto:michael.wise@uwa.edu.au">michael.wise@uwa.edu.au</a>. *(PhD Co-Supervisor)*
4. **Dr. Ibrahim Radwan** — Associate Professor, Faculty of Science and Technology, University of Canberra, ACT, Australia. <a href="mailto:ibrahim.radwan@canberra.edu.au">ibrahim.radwan@canberra.edu.au</a>. *(Research Collaborator)*
5. **Dr. Naveed Akhtar** — Senior Lecturer / DECRA Research Fellow, School of Computing &amp; Information Systems, University of Melbourne. <a href="mailto:naveed.akhtar1@unimelb.edu.au">naveed.akhtar1@unimelb.edu.au</a>. *(PhD Co-Supervisor)*

---

For a fully formatted PDF version, see the [resume in this repository]({{ '/' | relative_url }}M.Ibrahim_UWA_Lecturer_Resume.pdf) or contact me directly.
