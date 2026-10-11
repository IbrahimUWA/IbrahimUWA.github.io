---
layout: default
title: Research
permalink: /research/
description: Research themes — High Performance Computing, LiDAR &amp; 3D vision, multimodal deep learning, remote sensing, and AI for precision agriculture.
---

# Research

My research programme combines **algorithmic innovation** in deep learning and parallel computing with **applied impact** in autonomous systems and precision agriculture. I work with raw multimodal sensor data — LiDAR, hyperspectral, multispectral, thermal, RGB, GNSS / IMU, IoT and satellite — and translate it into models and decision tools that scale from a single field plot to city-scale and state-scale deployments.

## Theme 1 — High Performance Computing for 3D Vision

Modern 3D and remote-sensing pipelines are bottlenecked by data volume, not algorithm complexity. I design **GPU-accelerated, parallel algorithms** that close this gap.

- **CUDA / OpenCL parallel cylindrical scanning** for 3D LiDAR point clouds (CylinMamba3D, manuscript in preparation) — geometry-aware state-space modelling with end-to-end GPU pipelines.
- **Pawsey Setonix supercomputing** workflows for terabyte-scale UAV LiDAR and multispectral processing using Dask, Spark and SLURM.
- **Distributed analytics on Azure and AWS** for multimodal precision agriculture data integrating multispectral, weather, soil and yield datasets.
- Earlier work on **FPGA and GPU implementations of Fast Fourier Transform** (ICE Cube, 2016) and HPC laboratory infrastructure design at FAST-NUCES, Pakistan.

## Theme 2 — LiDAR and 3D Scene Understanding

This was the focus of my PhD and remains a flagship theme. I have built **public benchmark datasets** and developed **state-of-the-art deep models** that are now used internationally.

- **Datasets**: PC-Urban (4.3 B points, 25 classes), SWAN (16 B points, 24 classes, 10 k frames), Perth-WA Localization (30 k frames with 6DoF poses) — published on IEEE Dataport.
- **Models**: SAT3D (Slot Attention Transformer for semantic segmentation, *IEEE TITS* 2023), Slice Transformer (self-supervised 6DoF localization, *ICRA* 2023), UnLoc (unified LiDAR / Camera / Radar localization, *IROS* 2023), MuStD (multi-stream 3D object detection, *IROS* 2025).
- **2026 directions**: hypergraph-guided Mamba for foliage separation, dynamic time warping for sensor alignment, geometry-aware cylindrical SSM, structured latent flow for city-scale 3D generation.

## Theme 3 — Multimodal Remote Sensing &amp; Precision Agriculture

I lead the design of **AI-driven decision-support systems** that integrate satellite, drone, IoT and ground-truth data for Western Australia's agricultural sector — covering ~450,000 paddocks.

- **Spatial Hybrid Model for Crop Yield Prediction** (IGARSS 2025) integrating Sentinel-2, weather, soil and yield records with explainability via SHAP and PCA.
- **End-to-end UAV phenomics pipeline** for the Australian Plant Phenomics Network (APPN) — orthomosaicking, radiometric calibration, plot extraction, biomass / NDVI / GLI traits.
- **Plant-height and biomass estimation from LiDAR + VNIR** — [PhenoApp](/projects/) fuses per-plot LiDAR structure features with hyperspectral spectra through PCA feature families and a two-stream deep network (sparse 3D CNN + spectral transformer), reaching ~3 cm height RMSE on wheat trials; released with [CropLabel](/projects/) (SAM 3.1 plant / weed labelling) and [Plot Extractor](/projects/) in 2026.
- **SoilProfileNet** — deep learning that predicts volumetric soil water content at ten depths from electromagnetic-induction conductivity profiles (667 calibration cores, two WA seasons), replacing destructive coring.
- **Weed segmentation benchmarks** (BAWSeg / *Remote Sensing* 2026; DICTA 2024) at >90 % accuracy.

## Theme 4 — Multimodal Robotics, Autonomy and Smart Cities

- **3D city mapping with sensor fusion** of LiDAR + GNSS + IMU using Dynamic Time Warping for fine alignment (*IEEE JSTARS* 2026, published).
- **City-scale 3D change detection** (*Scientific Reports*, under review; code and the 20-pair Subiaco benchmark released) for urban planning and infrastructure monitoring.
- **Object detection for autonomous driving** via multistream LiDAR + camera fusion (IROS 2025).

## Theme 5 — LLMs, Prompt Engineering &amp; AI for Science

I treat large language models as **first-class scientific tools**: for code generation in HPC, automated documentation, agentic data pipelines, and pedagogy. I am developing teaching materials that combine **shell scripting + LLM prompting** for open-source tooling courses (CITS4407 style), and I incorporate LLM-assisted development in my supervision of HDR students.

## Funding &amp; Compute Resources

- **University of Jeddah Research Grant** — A$80,000-equivalent (200,000 SAR), 2025–2027, "3D Scene Understanding using LiDAR Sensor" (Grant UJ-24-SUTU-1290). *Co-Investigator.*
- **Pawsey Supercomputing Research Centre** — 2× allocations 2025–2026 (Reference A001647 Acacia storage, A001653 Nebula remote visualisation). Combined value ~**A$150,000** in compute &amp; storage. *Lead Applicant.*
- **Food Agility CRC — Agri-analytics Hub** — multi-institutional project (Curtin University, NGIS, DPIRD) covering ~450,000 WA paddocks.
- **DARPA / UCF Joint Project** — part-time data scientist (2020–2022).

## Collaborations

- **University of Western Australia** — Prof. Ajmal Mian (Computer Science), Prof. Michael Wise (Computer Science), Dr. Khyber Alam (Optometry), Dr. Mithran Goonewardene (Dental School).
- **Curtin University** — CCSDM &amp; NGIS (Agri-analytics Hub).
- **University of Melbourne** — Dr. Naveed Akhtar (Computing &amp; Information Systems).
- **University of Jeddah, Saudi Arabia** — multi-investigator LiDAR research programme.
- **Australian Plant Phenomics Network (APPN)**.
- **Forest Products Commission, Western Australia** — radiata pine plantation analytics.
