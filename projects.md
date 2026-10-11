---
layout: default
title: Projects &amp; Funding
permalink: /projects/
description: Active research projects, grants, datasets, open-source software and applications developed by Dr. Muhammad Ibrahim.
---

# Projects &amp; Funding

I lead and contribute to a portfolio of computer science projects in remote sensing, robotics, high-performance computing, big data processing, cloud computing, 3D vision, and multimodal data, spanning autonomous systems, smart cities, plant phenomics, clinical imaging and decision-support tools. Below are featured research systems with their architectures, the applications I have built (with their front ends), the most active projects, and the funded compute and research grants behind them. Most of the software is on GitHub under <a href="https://github.com/IbrahimUWA" target="_blank" rel="noopener">IbrahimUWA</a> and the DPIRD / APPN organisation <a href="https://github.com/appndpird" target="_blank" rel="noopener">appndpird</a>.

## Featured AI &amp; research systems

<div class="proj">
  <h3>GridFlow — City-Scale 3D Point Cloud Generation</h3>
  <div class="proj-meta">
    <span class="pill flagship">ECCV 2026 · Published</span>
    <span class="pill">Generative 3D</span>
    <span class="pill">Flow matching + Diffusion</span>
  </div>
  <p>A multi-stage generative framework that synthesises dense, coloured city-scale 3D point clouds (100k points per 150&nbsp;m tile) conditioned on satellite imagery, semantic maps and digital surface models. A <strong>Grid-Aligned VAE</strong> compresses each tile into a topology-preserving latent grid so adjacent tiles join seamlessly; a conditional <strong>rectified-flow</strong> model generates geometry and an orientation-aware <strong>diffusion</strong> model colourises it. Released with the <em>City3D-MultiGen</em> benchmark (163k tiles, Melbourne &amp; London). Best Chamfer Distance (−29% vs. PVD) and ~4× lower JSD than prior art.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/gridflow.png' | relative_url }}" alt="GridFlow conditioning and generation pipeline" loading="lazy">
    <figcaption><b>Pipeline (from the paper):</b> satellite imagery, semantic maps and DSM are converted into a grid-aligned condition; a Grid-Aligned VAE, conditional rectified flow and orientation-aware diffusion then generate the coloured city-scale point cloud.</figcaption>
  </figure>
  <p class="proj-links"><a href="https://doi.org/10.1007/978-3-032-37432-5_37" target="_blank" rel="noopener">DOI (LNCS, ECCV 2026, pp. 656–673) ↗</a></p>
</div>

<div class="proj">
  <h3>LiDAR-based 3D Change Detection at City Scale</h3>
  <div class="proj-meta">
    <span class="pill review">Scientific Reports · Under review</span>
    <span class="pill">Code + data released</span>
    <span class="pill">Smart cities</span>
  </div>
  <p>An <strong>uncertainty-aware, object-centric</strong> method for detecting what changed between two mobile-LiDAR surveys of a whole city. The two epochs are aligned coarse-to-fine (multi-resolution NDT, then point-to-plane ICP with a Tukey kernel); a per-point <strong>95% level of detection</strong> derived from the registration covariance and local surface roughness gates every decision so residual misalignment is never read as change. Unsupervised geometric segmentation yields <em>ground / building / vegetation / mobile</em> instances, which are matched per class with a Hungarian assignment and labelled <em>Added, Removed, Increased, Decreased</em> or <em>Unchanged</em> in 80&nbsp;m tiles. Validated on Subiaco (WA), surveyed in July 2023 (Ouster OS1-64) and February 2025 (OS1-128 + RTK GNSS/IMU): <strong>95.3% accuracy, 90.8% macro F1, 82.9% macro IoU</strong> over 20 loops, beating the strongest learning-based baseline (Triplet KPConv) without any training data.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/cd_overview.jpg' | relative_url }}" alt="Location of the 20 change-detection pairs inside the five 2023 Subiaco source maps" loading="lazy">
    <figcaption><b>Benchmark layout (from the repository):</b> the 20 co-registered 2023/2025 pairs (black: manual Pair1–8, red: automated Pair9–20, 80&nbsp;m × 80&nbsp;m) inside the five 2023 SLAM source maps (533&nbsp;M points; the 2025 survey holds 1.02&nbsp;B points over 20 loops).</figcaption>
  </figure>
  <p class="proj-links">
    <a href="https://arxiv.org/abs/2510.21112" target="_blank" rel="noopener">arXiv ↗</a> ·
    <a href="https://github.com/IbrahimUWA/LiDAR-3D-Change-Detection-City-Scale" target="_blank" rel="noopener">Code (MIT) ↗</a> ·
    <a href="https://huggingface.co/datasets/ibrahim80876/Change-Detection-LiDAR-Dataset" target="_blank" rel="noopener">Processed pairs on Hugging Face (CC BY 4.0, ~7 GB) ↗</a> ·
    <a href="https://ieee-dataport.org/documents/2023-subiaco-wa-3d-hd-lidar-point-cloud-maps-dataset" target="_blank" rel="noopener">2023 survey ↗</a> ·
    <a href="https://ieee-dataport.org/documents/2025-subiaco-wa-3d-hd-lidar-gnss-point-cloud-maps-dataset" target="_blank" rel="noopener">2025 survey ↗</a>
  </p>
</div>

<div class="proj">
  <h3>Hierarchical Multi-Scale Transformer–Mamba — Crop-Yield Prediction</h3>
  <div class="proj-meta">
    <span class="pill review">IEEE TGRS · Under review</span>
    <span class="pill">First author</span>
    <span class="pill">~450,000 paddocks</span>
  </div>
  <p>A hierarchical, multi-scale yield model for Western Australia built on a <strong>parallel Transformer–Mamba</strong> encoder (6 Transformer layers / 4 Mamba blocks, d = 256) with a <strong>slot-attention</strong> fusion bottleneck (6 slots). A per-crop base model trained at paddock scale is specialised to the administrative shire scale (area-weighted aggregation calibrated against GRDC statistics under a hybrid loss) and to the within-field sub-paddock scale (fine-tuned on ~1.3&nbsp;M yield-monitor points). Introduces the <em>WA Paddock Dataset</em> (142 soil, weather and Sentinel-2 features per paddock, reduced to 41 by SHAP, ~450k paddocks, seasons 2020–2023, wheat / canola / barley) and reaches paddock-level R² up to 0.95 with stable season-to-season accuracy.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/cropyield.png' | relative_url }}" alt="Hierarchical multi-scale Transformer-Mamba crop-yield architecture" loading="lazy">
    <figcaption><b>Architecture (from the paper):</b> (a) the paddock base model fuses WA Paddock features after SHAP preprocessing, feeds parallel Transformer and Mamba streams, and combines them through a slot-attention bottleneck; (b) the trained model is fine-tuned to shire and sub-paddock scales; (c) spatial inference fuses the three scales into a state-wide yield surface.</figcaption>
  </figure>
  <p class="proj-links"><a href="https://github.com/IbrahimUWA/Hierarchical-MultiScale-Crop-Yield-WA" target="_blank" rel="noopener">GitHub repository (method, data and experimental setup; full code and the WA Paddock Dataset are released on acceptance) ↗</a> · <a href="https://doi.org/10.1109/IGARSS55030.2025.11243086" target="_blank" rel="noopener">Precursor paper, IGARSS 2025 ↗</a></p>
</div>

<div class="proj">
  <h3>Geo-Registration of LiDAR Point Clouds without GNSS</h3>
  <div class="proj-meta">
    <span class="pill published">IEEE JSTARS · Published</span>
    <span class="pill">Second author</span>
    <span class="pill">Cross-modal alignment</span>
  </div>
  <p>A fully automatic method that geo-registers terrestrial LiDAR point clouds to satellite imagery in <strong>GNSS-denied</strong> urban environments. Road points are segmented with a Point Transformer, road skeletons and intersections are matched across the LiDAR and satellite views, then a global rigid alignment is refined by a non-rigid thin-plate-spline warp and corrected against SRTM terrain. On KITTI it reduces mean planimetric error from 2.60&nbsp;m to 0.69&nbsp;m — better than the raw GNSS annotations — and is validated on a new Perth CBD dataset.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/georeg.png' | relative_url }}" alt="GNSS-free geo-registration pipeline (from the paper)" loading="lazy">
    <figcaption><b>Pipeline (from the paper):</b> parallel point-cloud and map branches segment roads, skeletonise and extract intersections, then perform global rigid alignment, non-rigid thin-plate-spline refinement and SRTM-based elevation correction.</figcaption>
  </figure>
  <p class="proj-links"><a href="https://doi.org/10.1109/JSTARS.2026.3733746" target="_blank" rel="noopener">DOI ↗</a></p>
</div>

<div class="proj">
  <h3>DHMamba — Hypergraph-Guided Mamba for Foliage Separation</h3>
  <div class="proj-meta">
    <span class="pill published">IEEE JSTARS · Published</span>
    <span class="pill">Code released</span>
    <span class="pill">Forestry / TLS</span>
  </div>
  <p>Leaf–wood separation of terrestrial laser-scanning forest point clouds using a linear-complexity <strong>Mamba</strong> backbone paired with a <strong>dynamic hypergraph</strong> serialization that captures higher-order topological dependencies. Density and geometric priors (planarity, linearity) sharpen multi-scale discrimination of fine branches and leaves. Beats Transformer baselines in mIoU across seven datasets while processing ~5× larger patches under equal memory.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/foliage.png' | relative_url }}" alt="DHMamba foliage separation pipeline (from the paper)" loading="lazy">
    <figcaption><b>Pipeline (from the paper):</b> FPS / KNN density-aware patches and global density / scale priors feed token embedding, dynamic hypergraph convolution (high / low-density tokens) and a stack of Mamba blocks for point-wise leaf / wood separation.</figcaption>
  </figure>
  <p class="proj-links"><a href="https://doi.org/10.1109/JSTARS.2026.3696349" target="_blank" rel="noopener">DOI ↗</a> · <a href="https://github.com/ZhangIceNight/foliage_segmentation" target="_blank" rel="noopener">Code ↗</a></p>
</div>

<div class="proj">
  <h3>CylinMamba3D — Geometry-Aware Cylindrical State-Space Modelling</h3>
  <div class="proj-meta">
    <span class="pill">Manuscript in preparation</span>
    <span class="pill">CUDA / OpenCL</span>
    <span class="pill">3D deep learning</span>
  </div>
  <p>A geometry-aware <strong>Mamba</strong> framework for 3D point clouds that resolves the mismatch between the unordered nature of points and the sequential order required by state-space models. Token centres are projected to cylindrical (r, θ, z) coordinates and serialized to give a geometry-consistent traversal; a Cylindrical State-Space Module handles long-range propagation while a local module refines geometry. Achieves 94.0% accuracy on ModelNet40 with linear-time efficiency and a GPU-parallel CUDA / OpenCL implementation.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/cylinmamba.png' | relative_url }}" alt="CylinMamba3D architecture: cylindrical 3D Mamba encoder with C-SSM and LNP" loading="lazy">
    <figcaption><b>Architecture (from the manuscript):</b> after FPS / KNN tokenization and cylindrical coordinate transformation, a stack of Cylindrical 3D Mamba blocks (each pairing a C-SSM global module with local neighbourhood processing) feeds a classification / segmentation head.</figcaption>
  </figure>
</div>

## Applications &amp; tools I have built

Production software developed for DPIRD, the Australian Plant Phenomics Network (APPN), UWA and clinical partners. Each entry shows the actual front end of the application.

<div class="proj">
  <h3>PhenoApp v3.3.2 — Plant Phenotyping from UAV LiDAR and VNIR Hyperspectral Data</h3>
  <div class="proj-meta">
    <span class="pill app">Desktop application · PyQt5</span>
    <span class="pill">LiDAR + VNIR fusion</span>
    <span class="pill">Height &amp; biomass models</span>
    <span class="pill">Released 10 Oct 2026</span>
  </div>
  <p>A 13-tab desktop application (Python / PyQt5, PyInstaller Windows build) that turns a raw UAV LiDAR point cloud and a VNIR hyperspectral cube into per-plot traits and calibrated <strong>plant-height and above-ground-biomass predictions</strong> for field trials. Developed for the APPN DPIRD node under the supervision of Dr. Hammad Khan.</p>
  <ul>
    <li><strong>Plots and traits:</strong> SMRF ground classification, canopy raster, 4-corner grid generation, drag / rotate / scale plot editing over the canopy, per-plot clipping and <strong>23 physical traits</strong>; LiDAR v3 preprocessing classifies every point (noise / ground / low vegetation / canopy), with a selectable noise rule and 20&nbsp;cm-interior gap metrics (P<sub>gap</sub>, LAI proxy, 2&nbsp;cm cover) that are robust to alley soil inside refit polygons.</li>
    <li><strong>VNIR Spectral tab:</strong> ~200 indices from the Awesome Spectral Indices catalogue plus narrow-band extras, computed per plot on pixel-exact per-plot cubes, with a flight-level reflectance check, red-clipping censoring and a NaN rule that keeps unusable bands out of every table.</li>
    <li><strong>Height Models tab:</strong> linear calibration on cth<sub>p95</sub>, ridge / random forest / XGBoost on canopy-structure features, and v3 sets — LiDAR core (22 features), LiDAR + VNIR (43), and PCA families (per-modality late fusion or joint early fusion) with PLS, ridge, Gaussian process and random forest under nested repeated 10-fold validation.</li>
    <li><strong>Biomass ML tab:</strong> fused LiDAR + VNIR feature families (LiDAR_core, VNIR_core, Fused_core, Fused_all, LiDAR / VNIR / Fused PCA, joint PCA, band-spectrum PCA) × 8 learners (ridge, PLS, SVR, GPR, random forest, extra trees, XGBoost, LightGBM), nested feature selection, saved pipelines, and "apply a saved model" to a new flight with an offset calibrated on a few measured plots.</li>
    <li><strong>Deep Models tab:</strong> a <strong>two-stream network</strong> (sparse 3D CNN on the classified per-plot point cloud + spectral transformer on the per-plot VNIR spectrum with a band-availability mask) trained with a <strong>common 111-band policy</strong>; bundled pretrained 5-fold ensembles for biomass and height (two-stream and LiDAR-only), GPU auto-detection, and fine-tuning on a new trial.</li>
  </ul>
  <div class="fig-row">
    <figure class="proj-fig">
      <img src="{{ '/assets/figures/phenoapp_height_models.png' | relative_url }}" alt="PhenoApp v3.3.2 Height Models tab listing LiDAR, LiDAR+VNIR and PCA model families" loading="lazy">
      <figcaption>Height Models tab: LiDAR core, LiDAR + VNIR and PCA feature families with PLS / ridge / GPR / random-forest learners and repeated 10-fold validation.</figcaption>
    </figure>
    <figure class="proj-fig">
      <img src="{{ '/assets/figures/phenoapp_deep_models.png' | relative_url }}" alt="PhenoApp v3.3.2 Deep Models tab for the two-stream sparse 3D CNN + spectral transformer" loading="lazy">
      <figcaption>Deep Models tab: tensors from the project LAS + VNIR cube + grid, pretrained two-stream ensemble, predict or fine-tune.</figcaption>
    </figure>
  </div>
  <p><strong>Latest model results (9–10 Oct 2026 rebuild, held-out 10-fold, five UAV flights over two wheat trials):</strong></p>
  <table>
    <thead><tr><th>Target / trial</th><th>Best feature model (Height / Biomass ML tabs)</th><th>Two-stream network (LiDAR + VNIR)</th></tr></thead>
    <tbody>
      <tr><td>Plant height, anthesis flight (n = 128)</td><td>R² 0.59 · RMSE <strong>3.3 cm</strong> (joint PCA, ridge)</td><td>R² 0.46 · RMSE 3.7 cm</td></tr>
      <tr><td>Plant height, maturity flight (n = 128)</td><td>R² 0.55 · RMSE 3.4 cm (joint PCA, ridge)</td><td>R² 0.35 · RMSE 4.1 cm</td></tr>
      <tr><td>Biomass, trial A anthesis (n = 128)</td><td>R² 0.37 · RMSE 1,513 kg/ha (joint PCA, GPR)</td><td>R² 0.27 · RMSE 1,636 kg/ha</td></tr>
      <tr><td>Biomass, trial B anthesis (n = 252)</td><td>R² 0.19 · RMSE 1,374 kg/ha (band PCA, ridge)</td><td>R² 0.07 · RMSE 1,467 kg/ha</td></tr>
    </tbody>
  </table>
  <p class="flow-note">Within a trial the fused PCA feature models remain the best choice; the VNIR stream alone carries no within-trial signal, and the common-band policy equals or beats per-plot band sets. The deep ensembles are shipped for scoring new flights and for retraining once several hundred labelled plots are available.</p>
  <div class="flow">
    <div class="flow-step alt"><b>UAV LiDAR + VNIR</b>LAS / LAZ + ENVI cube</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Ground &amp; plots</b>SMRF · grid · edit</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Features</b>23 traits · LiDAR v3 · ~200 indices</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Models</b>PCA families · 8 learners · two-stream DL</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>Per-plot outputs</b>Height · biomass · QC · LAS</div>
  </div>
  <p class="proj-links"><a href="https://github.com/appndpird/DESKTOP-POINTCLOUD-APP" target="_blank" rel="noopener">GitHub repository (source, user guide, research scripts and saved models) ↗</a></p>
</div>

<div class="proj">
  <h3>CropLabel — SAM3.1-Assisted Instance &amp; Semantic Labelling of Crop Plots</h3>
  <div class="proj-meta">
    <span class="pill app">Web application · FastAPI</span>
    <span class="pill">SAM 3.1 · PyTorch</span>
    <span class="pill">Agentic labelling</span>
    <span class="pill">Released Sep 2026</span>
  </div>
  <p>An <strong>agentic labelling tool</strong> for UAV crop-plot tiles that produces instance and semantic segmentation of <em>crop plants, weeds and soil</em> with a handful of clicks. Soil is labelled automatically from the Excess Green index; clicking <strong>one example plant</strong> makes SAM&nbsp;3.1 find every similar plant in the image as a separate instance (Shift-click = negative example), and a free-text box runs any description ("broad leaf plant", "thin grass seedling") as a concept prompt. Every save trains a crop-vs-weed classifier on colour / shape / texture features, so <strong>"Label ALL remaining"</strong> auto-labels the rest of the folder with improving accuracy. Fourteen manual tools (polygon snapped to vegetation, brush, eraser, split by line / seeds / box / polygon / auto, merge, reclassify) correct the result with 25-step undo. Outputs: semantic index mask and uint16 instance map at the original size and filename, per-instance JSON, optional YOLO boxes, and per-image agronomic statistics (plants / m², weeds / m², crop cover, mean plant area) in <code>summary.csv</code>.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/croplabel_ui.png' | relative_url }}" alt="CropLabel browser interface: SAM, Create and Fix tool groups, class selector, find box and review options" loading="lazy">
    <figcaption>CropLabel front end: Auto-label, SAM / Create / Fix tool groups with keyboard shortcuts, crop / weed class selector, the "Find" concept-prompt box, review options (instance numbers, boxes, side-by-side) and batch "Label ALL remaining".</figcaption>
  </figure>
  <p class="proj-links"><a href="https://github.com/appndpird/CropLabel" target="_blank" rel="noopener">GitHub repository + user guide ↗</a></p>
</div>

<div class="proj">
  <h3>RetinaLabel — SAM3-Assisted Disease Labelling for Ultra-Widefield Retinal Images</h3>
  <div class="proj-meta">
    <span class="pill app">Web application · FastAPI</span>
    <span class="pill">SAM 3.1 · SAM 2.1 · RETFound</span>
    <span class="pill">Clinical imaging</span>
    <span class="pill">UWA Optometry</span>
  </div>
  <p>A labelling tool built so <strong>clinic staff can annotate Optos retinal images (FAF + RG) with a few clicks</strong>, feeding the inherited-retinal-disease classification work with Dr. Khyber Alam and Prof. Fred Chen. Each FAF / RG pair is cropped to the retina and downsampled with the same window so masks transfer 1:1 (and back to the original 3997 × 3989 resolution). SAM&nbsp;3.1 proposes <em>disease</em> and <em>optic-nerve</em> regions from text prompts; smart click / box, brush, eraser, region delete, move and reclassify tools correct them; an <strong>exemplar "find similar" tool</strong> labels every lesion resembling one example (0.90 precision / 0.96 recall against a full manual mask); a retina-only ROI excludes eyelash shadows. After three reviewed images an adaptive pixel classifier trained on the corrected labels, and optionally a fine-tuned RETFound segmentation head, assist every later auto-label, and a batch mode labels the remaining queue overnight. Outputs include index / colour / overlay masks, full-resolution masks, optic-nerve centres in both coordinate frames and a per-eye <code>labels.csv</code>. Additional disease classes (RCD, Stargardt, Choroideremia, Best disease, …) are managed in the toolbar.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/retinalabel_ui.png' | relative_url }}" alt="RetinaLabel browser interface with Auto-label (SAM3), smart tools, class selector and Save & transfer to RG" loading="lazy">
    <figcaption>RetinaLabel front end: patient queue, Auto-label (SAM3), smart add / remove, box, brush, eraser, delete, move, reclassify, find-similar and ROI tools, prompt editor, RG view toggle and "Save &amp; transfer to RG".</figcaption>
  </figure>
  <p class="proj-links">Code: private repository (patient data governance) — available to collaborators on request. Companion research prototype <strong>RetinaDiffusion</strong>: a conditional latent diffusion model (frozen SD-VAE, 88.6&nbsp;M-parameter UNet, v-prediction, classifier-free guidance) that generates a patient's <em>future</em> Optos image from an earlier visit conditioned on the time gap, disease, modality and eye, trained on ORB + RANSAC-registered longitudinal series with a patient-wise split.</p>
</div>

<div class="proj">
  <h3>Plot Extractor — One Geotagged Raw Image per Plot from Metashape or an Orthomosaic</h3>
  <div class="proj-meta">
    <span class="pill app">Desktop application · Tkinter</span>
    <span class="pill">Agisoft Metashape API · GDAL</span>
    <span class="pill">Photogrammetry</span>
    <span class="pill">Released Sep 2026</span>
  </div>
  <p>A desktop tool that extracts <strong>one raw image per plot</strong> (and optionally a deskewed orthomosaic crop per plot) from an Agisoft Metashape project, or straight from a GeoTIFF orthomosaic with no licence, using a plot-boundary shapefile / GeoJSON in any CRS. For every plot the polygon is dropped onto the DEM and back-projected into every aligned camera; cameras are scored by the exact share of the plot they image and the best frame is cropped. Six raw-crop styles, from a bit-identical native crop to a <strong>rectified rectangle</strong> built by mesh-based rectification with the full camera model (perspective + lens distortion) — which reduced inter-frame disagreement from up to 37&nbsp;mm on the ground to under 1&nbsp;mm — and <strong>seamless stitching</strong> that routes a minimum-error seam across bare soil and applies only a feathered brightness offset, so every pixel still comes from exactly one frame and no plant is ghosted. GeoTIFF outputs carry WGS84 GCPs and source EXIF; runs are deterministic and parallel across CPU cores. A second tab designs the plot grid itself from four clicked trial corners over the orthomosaic, with an interactive plot editor (grow / shrink, drag corners, multi-select resize) and a tiler for training tiles.</p>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/plotextractor_ui.png' | relative_url }}" alt="Plot Extractor main window: source selection, Metashape project, plot boundaries, output options and crop styles" loading="lazy">
    <figcaption>Plot Extractor front end: source (Metashape project or orthomosaic), plot boundaries and ID attribute, raw-crop style and engine, rectification grid, seamless stitching, CPU cores, and the Generate-plot-grid and Training-tiles tabs.</figcaption>
  </figure>
  <p class="proj-links"><a href="https://github.com/appndpird/plot-extractor" target="_blank" rel="noopener">GitHub repository + user guide ↗</a> · <a href="https://github.com/appndpird/plot-extractor/releases" target="_blank" rel="noopener">Windows releases ↗</a></p>
</div>

<div class="proj">
  <h3>Pawsey Data Management App (PDMA) v2.5.1 — Research Data to Supercomputing Storage</h3>
  <div class="proj-meta">
    <span class="pill app">Desktop application · Tkinter</span>
    <span class="pill">rclone · S3 · SigV4</span>
    <span class="pill">HPC data management</span>
    <span class="pill">Formerly Pawsey Uploader</span>
  </div>
  <p>A single-file Python / Tkinter application (no third-party packages at run time; Windows and Linux builds) that manages terabyte-scale research data on the <strong>Pawsey Supercomputing Centre's Acacia S3 object storage</strong>, from where it is processed on <strong>Setonix</strong> and explored on <strong>Nebula</strong> remote visualisation — saving ~A$150k versus commercial cloud. Started as an uploader in June 2026 and grown through 15 releases into a full data-management tool:</p>
  <ul>
    <li><strong>Transfers:</strong> one-way copy, exact mirror and OneDrive-style <strong>two-way sync</strong> (rclone bisync) with conflict policies, rename detection, checksum verification, a safety cap on deletions, a soft-delete <strong>recycle bin</strong> that doubles as version history, scheduled auto-sync, preview (dry-run) by default, and a two-pass "verify both sides" that also compares folder trees.</li>
    <li><strong>Unattended operation:</strong> auto-restart on transient failures, smart detection of non-retryable errors, baseline recovery for two-way sync, multi-slot resume, heartbeat file, per-transfer logs and a diagnostics log.</li>
    <li><strong>Empty folders on object storage:</strong> directory markers in every mode and direction, including folders that are themselves empty.</li>
    <li><strong>Storage management:</strong> Windows-style copy / cut / paste and rename as server-side moves, bucket management, usage charts, multi-project credentials, and <strong>"Send to another project"</strong> as a resumable background job.</li>
    <li><strong>Sharing and publishing:</strong> temporary presigned links (hand-rolled SigV4, up to 7 days) and <strong>permanent public links</strong> for published datasets, with a generated browser page that downloads a whole dataset, a folder or a file, preserving folder structure, plus an optional single-ZIP snapshot.</li>
    <li><strong>Rename / Match (v2.5):</strong> folders renamed on the PC after upload are matched to their Pawsey copy by <em>content</em> (names + sizes, MD5 spot-checks) and renamed server-side instead of re-uploading hundreds of gigabytes, with live progress and recovery of interrupted moves.</li>
  </ul>
  <figure class="proj-fig">
    <img src="{{ '/assets/figures/pdma_ui.png' | relative_url }}" alt="PDMA v2.5 Rename / Match tab matching local and Pawsey folders by content" loading="lazy">
    <figcaption>PDMA front end (Rename / Match tab): a 110&nbsp;GB site folder renamed locally is matched to its Pawsey copy by content and renamed server-side instead of being re-uploaded.</figcaption>
  </figure>
  <div class="flow">
    <div class="flow-step alt"><b>Field data</b>Local terabyte-scale captures</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>PDMA</b>Copy · mirror · two-way sync</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Acacia S3</b>Pawsey object storage</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Setonix HPC</b>Parallel processing</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>Share / publish</b>Links · Nebula visualisation</div>
  </div>
  <p class="proj-links"><a href="https://github.com/appndpird/pawsey-uploader" target="_blank" rel="noopener">GitHub repository ↗</a> · <a href="https://github.com/appndpird/pawsey-uploader/releases" target="_blank" rel="noopener">Releases (v2.5.1 latest) ↗</a></p>
</div>

<div class="proj">
  <h3>UoJ LiDAR Scene-Understanding Platform &amp; LiDAR Scene Annotator Desktop</h3>
  <div class="proj-meta">
    <span class="pill app">Web + desktop application</span>
    <span class="pill">Three.js · FastAPI · React · Electron</span>
    <span class="pill">Bilingual EN / AR</span>
  </div>
  <p>An interactive web platform and 3D annotation prototype for outdoor LiDAR scene understanding, built for the University of Jeddah research programme. A browser-based Three.js / WebGL viewer renders large point clouds for interactive semantic annotation, with a FastAPI backend managing datasets and labels and a React front end providing a bilingual (English / Arabic) interface — feeding curated labels into segmentation-model training. The same stack has been packaged as a <strong>cross-platform Electron desktop app</strong> ("LiDAR Scene Annotator") that runs fully offline: semantic segmentation and 3D object detection from one placed geometry, brush / polygon / sphere / cylinder / box editors, AI assist (auto-cuboid, smart-detect, smart-lasso, ground segmentation, Cylinder3D / MinkUNet / PointPillars / CenterPoint back ends with a geometric CPU fallback), active-learning refinement, multi-frame episodes from <code>.pcap</code> with label propagation and tracking, and project save / load. The desktop app will be released publicly with the accompanying survey paper.</p>
  <div class="fig-row">
    <figure class="proj-fig">
      <img src="{{ '/assets/figures/uoj_annotate.png' | relative_url }}" alt="UoJ LiDAR platform annotation workspace" loading="lazy">
      <figcaption>Annotation workspace with in-browser point-cloud viewer, runtime and method configuration (Cylinder3D / voxel-based segmentation).</figcaption>
    </figure>
    <figure class="proj-fig">
      <img src="{{ '/assets/figures/uoj_bilingual.png' | relative_url }}" alt="UoJ LiDAR platform bilingual English/Arabic interface" loading="lazy">
      <figcaption>Bilingual English / Arabic class labels with a live per-class score summary.</figcaption>
    </figure>
  </div>
</div>

<div class="proj">
  <h3>HTP Project Manager v1.8.0 — APPN UAV Project Data Organisation (DPIRD node)</h3>
  <div class="proj-meta">
    <span class="pill app">Desktop application</span>
    <span class="pill">FAIR data</span>
    <span class="pill">Contributor · DPIRD node release</span>
  </div>
  <p>The DPIRD-node version of the APPN project-management desktop UI (upstream: APPN-UQ). It creates project and site folder structures on the shared data store, attaches KML, shapefiles, GCPs and trait files to sites, and stages raw UAV flight data into sensor / date / run buckets, so every capture is FAIR-ready and metadata-rich before it moves to Pawsey through PDMA. I developed the v1.7.x–v1.8.0 series published as the DPIRD release (self-contained Windows build, user guide, change log).</p>
  <div class="flow">
    <div class="flow-step alt"><b>Raw captures</b>UAV imagery / sensors</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Project / site</b>Standard folder tree</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Metadata</b>KML · shapefiles · GCPs · traits</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Staging</b>Sensor / date / run buckets</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>FAIR dataset</b>Publish via PDMA to Pawsey</div>
  </div>
  <p class="proj-links"><a href="https://github.com/appndpird/ProjectManageAPP" target="_blank" rel="noopener">GitHub repository ↗</a> · <a href="https://github.com/appndpird/ProjectManageAPP/releases" target="_blank" rel="noopener">v1.8.0 release ↗</a></p>
</div>

<div class="proj">
  <h3>DotTrack — Mobile Video Labelling for Detection &amp; Tracking</h3>
  <div class="proj-meta">
    <span class="pill app">Android application</span>
    <span class="pill">Annotation</span>
    <span class="pill">Detection / tracking</span>
  </div>
  <p>An Android application (tested on Samsung Galaxy S25) for annotating objects in video to build object-detection and tracking datasets. Users import or capture video, draw and adjust bounding boxes frame by frame with touch-replay and timeline drag-select gestures, propagate boxes across frames, and export annotations in standard formats. A fork adds on-device AI tracking (ViT tracker via ONNX Runtime) and a companion SAM&nbsp;3.1 / YOLO web app for multi-object labelling.</p>
  <div class="flow">
    <div class="flow-step alt"><b>Video</b>Capture / import</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Frame view</b>Frame-by-frame scrub</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Annotate</b>Draw &amp; adjust boxes</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Track</b>Propagate across frames</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>Export</b>Detection / tracking labels</div>
  </div>
</div>

<div class="proj">
  <h3>FlowerPower — Flowering-Date Prediction (AWS)</h3>
  <div class="proj-meta">
    <span class="pill app">Web application</span>
    <span class="pill">AWS</span>
    <span class="pill">Agronomy</span>
  </div>
  <p>A decision-support web application that predicts crop flowering dates from weather-station data using generalised additive and machine-learning models, presented through an interactive dashboard. I am responsible for maintaining, updating and deploying the system on <strong>AWS</strong> for ongoing seasonal use by agronomists, including the 2025 barley model refresh and its front end.</p>
  <div class="flow">
    <div class="flow-step alt"><b>Weather data</b>Station time series</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Models</b>GAM / ML predictors</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Prediction</b>Flowering date by variety</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Dashboard</b>Interactive web UI</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>Deploy</b>AWS hosting</div>
  </div>
</div>

<div class="proj">
  <h3>Dental School Bone-Quality Visualisation Tool (UWA)</h3>
  <div class="proj-meta">
    <span class="pill app">Desktop application</span>
    <span class="pill">Python · PyQt5 · VTK</span>
    <span class="pill">Clinical analysis</span>
  </div>
  <p>A Python desktop application developed with the UWA Dental School for visualisation and clinical examination of tooth quality and statistical analysis of bone and soft tissue near the midline of the front teeth on CT volumes, now extended to measure mid-palatal bone density (Hounsfield units) in anterior / middle / posterior regions for surgically assisted maxillary expansion studies. It is used by Master's and PhD students in the school.</p>
  <div class="flow">
    <div class="flow-step alt"><b>Scan data</b>CT / DICOM volumes</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Midline</b>Reference detection</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Measure</b>Bone &amp; soft-tissue metrics</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step"><b>Statistics</b>Comparative analysis</div>
    <div class="flow-arrow">→</div>
    <div class="flow-step accent"><b>Report</b>Clinical visualisation</div>
  </div>
</div>

## Active research projects

### Australian Plant Phenomics Network (APPN) — DPIRD node

National Research Infrastructure for **high-throughput, FAIR-aligned plant phenotyping**.

- Built an **end-to-end UAV imagery pipeline** (orthomosaic, geo-correction, radiometric calibration, vegetation classification, biomass / NDVI / GLI traits) hosted on Pawsey supercomputing.
- Released a family of open tools for the node in 2026: **PhenoApp** (LiDAR + VNIR height and biomass models), **CropLabel** (SAM&nbsp;3.1 crop / weed / soil labelling), **Plot Extractor** (per-plot raw and ortho crops from Metashape), **PDMA** (Pawsey data management) and the **HTP Project Manager** DPIRD release — see above.
- Working across **LiDAR, VNIR hyperspectral, mm-resolution Phase-One RGB, IoT sensors** for weather / soil, and **Sentinel-2** via Google Earth Engine; two Pawsey allocations (30&nbsp;TB managed storage + Nebula remote visualisation) underpin the data flow.
- Completed a structured literature review of plant-height and biomass estimation from LiDAR, RGB, multispectral and fused UAV data (74 papers, 2020–2026) that guides the APPN algorithm work package.

### Agri-analytics Hub — Food Agility CRC (June 2024 – June 2025)

A multi-institutional digital decision-support platform integrating **satellite, soil, weather and yield datasets** across **~450,000 paddocks** in Western Australia. Partners: **DPIRD, Curtin University CCSDM, NGIS**.

- Co-developed the spatial hybrid yield-prediction model (Transformers / CNNs / Mamba) — published at **IGARSS 2025** and extended to the hierarchical multi-scale model now under review at *IEEE TGRS*.
- Applied PCA and SHAP-based explainability to identify yield drivers and quantify productivity opportunities.
- Designed scenario-analysis workflows and interactive dashboards for stakeholder-facing decision support.

### 3D City Mapping &amp; Scene Understanding (UWA Adjunct programme)

Working with **Prof. Ajmal Mian** and international partners (University of Jeddah) on the next generation of city-scale 3D perception.

- Multi-sensor LiDAR + GNSS + IMU fine alignment via Dynamic Time Warping (*IEEE JSTARS* 2026, published).
- GNSS-free geo-registration of LiDAR to satellite imagery (*IEEE JSTARS* 2026, published).
- City-scale 3D change detection (*Scientific Reports*, under review; arXiv, code and the 20-pair Subiaco benchmark released, Sep 2026).
- Structured latent flow for 3D city-scale point cloud generation — GridFlow (*ECCV 2026*, published).
- GPU-parallel cylindrical state-space modelling — CylinMamba3D (manuscript in preparation).
- A comprehensive survey of outdoor 3D scene understanding with LiDAR (datasets, annotation, registration, mapping, segmentation, detection, tracking, localisation, completion and multimodal fusion), with the LiDAR Scene Annotator desktop app to be released alongside it.

### Root Phenotyping &amp; SoilProfileNet (July 2025 – present)

Deep learning that predicts **volumetric soil water content** at ten depths (5–95&nbsp;cm) from DUALEM electromagnetic-induction conductivity profiles, replacing destructive gravimetric coring. Trained on 667 calibration cores from two WA wheatbelt trials (2024 Meckering, 2025 calibration site) with diffusion-based tabular augmentation; the best deep models (DeepResNet, SoilFusionNet, SoilMamba) reach a combined R² ≈ 0.89 and produce shapefile-bounded plot moisture maps from each EMI survey. Manuscript in preparation for *Computers and Electronics in Agriculture*.

### Legacy Data Governance &amp; Analytics — DPIRD (Nov 2025 – present)

- Structuring and classifying **42 years** of historical crop datasets — establishing governance, metadata standards and publishing pathways; a publish-ready catalogue of a 40-year research archive was delivered to the Information, Planning &amp; Compliance team in 2026.
- Developed an executable comparative analytics tool evaluating **CSIRO and DPIRD predictive models** to support evidence-based executive investment decisions.

### Southern Rangelands Revitalisation Program (SRRP)

Processing drone-derived multispectral imagery into orthomosaics and 3D point clouds for **quantitative vegetation assessment**, with cost / feasibility analysis to guide technology adoption.

### Optometry AI Collaboration — UWA / Lions Eye Institute

With **Dr. Khyber Alam, Prof. Fred K. Chen** (UWA Optometry / Lions Eye Institute): AI-based classification of inherited retinal diseases from fundus autofluorescence and ultrawide retinal images (*Journal of Ophthalmology* 2026), the **RetinaLabel** SAM3-assisted labelling tool for clinic staff, and **RetinaDiffusion**, a conditional latent diffusion model that forecasts a patient's future retinal image from an earlier visit.

### Dental School Collaboration — UWA

In collaboration with **Mithran Goonewardene** and the orthodontics programme (UWA Dental School), developed the bone-quality visualisation tool above and a repeatability study of mid-palatal bone density measurements (ICC 0.99 for mean HU) supporting a manuscript on ossification after surgically assisted rapid maxillary expansion.

## Funded research &amp; compute grants

<ul class="pub-list">
  <li>
    <span class="tag gold">A$80k-equiv.</span>
    <strong>3D Scene Understanding using LiDAR Sensor</strong> — University of Jeddah, Saudi Arabia. Grant <strong>UJ-24-SUTU-1290</strong>. Awarded 2025. <em>200,000 SAR.</em>
  </li>
  <li>
    <span class="tag gold">~A$150k value</span>
    <strong>Pawsey Supercomputing Research Centre — 2× allocations</strong>:
    <em>(1) Remote Visualization and High-Memory Compute for APPN Crop Phenotyping (DPIRD)</em>, Reference A001653, Nebula Remote Visualisation, accepted April 2026; and
    <em>(2) Multimodal UAV Crop Phenotyping Data Storage for APPN (DPIRD node)</em>, Reference A001647, Managed Storage 30 TB, accepted April 2026.
    Combined commercial-cloud-equivalent value <strong>~A$150,000</strong>.
  </li>
  <li>
    <span class="tag">Industry / CRC</span>
    <strong>Food Agility CRC — Agri-analytics Hub</strong> (DPIRD / Curtin / NGIS), June 2024 – June 2025.
  </li>
  <li>
    <span class="tag">Federal (US)</span>
    <strong>DARPA / University of Central Florida joint project</strong> — Data Scientist (part-time, 2020–2022).
  </li>
</ul>

## Open datasets &amp; software

<div class="card-grid">
  <div class="card">
    <h3>SWAN Dataset</h3>
    <p>16 B points, 10,000 frames, 24 classes — Perth CBD, 64-channel Ouster LiDAR. <a href="https://ieee-dataport.org/documents/swan" target="_blank" rel="noopener">IEEE DataPort</a></p>
  </div>
  <div class="card">
    <h3>PC-Urban</h3>
    <p>4.3 B points, 66,000 frames, 25 semantic classes. <a href="https://ieee-dataport.org/documents/pc-urban-outdoor-dataset-3d-point-cloud-semantic-segmentation" target="_blank" rel="noopener">IEEE DataPort</a></p>
  </div>
  <div class="card">
    <h3>Perth-WA Localization</h3>
    <p>30,000 LiDAR frames with 6DoF pose annotations. <a href="https://ieee-dataport.org/documents/perth-wa-localization-dataset-3d-point-cloud-maps" target="_blank" rel="noopener">IEEE DataPort</a></p>
  </div>
  <div class="card">
    <h3>Subiaco 2023 &amp; 2025 City Maps</h3>
    <p>Bi-temporal mobile-LiDAR surveys of Subiaco, WA: 5 SLAM maps (533 M points, 2023) and 20 loops with GNSS logs (1.02 B points, 2025). <a href="https://ieee-dataport.org/documents/2023-subiaco-wa-3d-hd-lidar-point-cloud-maps-dataset" target="_blank" rel="noopener">2023</a> · <a href="https://ieee-dataport.org/documents/2025-subiaco-wa-3d-hd-lidar-gnss-point-cloud-maps-dataset" target="_blank" rel="noopener">2025</a></p>
  </div>
  <div class="card">
    <h3>Change-Detection LiDAR Dataset</h3>
    <p>20 co-registered 2023 / 2025 point-cloud pairs with alignment metadata (CC BY 4.0) and the MIT-licensed change-detection code. <a href="https://huggingface.co/datasets/ibrahim80876/Change-Detection-LiDAR-Dataset" target="_blank" rel="noopener">Hugging Face</a> · <a href="https://github.com/IbrahimUWA/LiDAR-3D-Change-Detection-City-Scale" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>WA Paddock Dataset</h3>
    <p>Soil, weather and Sentinel-2 features for ~450,000 WA paddocks, 2020–2023 — released with the TGRS paper. <a href="https://github.com/IbrahimUWA/Hierarchical-MultiScale-Crop-Yield-WA" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>PhenoApp</h3>
    <p>LiDAR + VNIR plant phenotyping desktop app with height / biomass models and pretrained two-stream ensembles. <a href="https://github.com/appndpird/DESKTOP-POINTCLOUD-APP" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>CropLabel</h3>
    <p>SAM 3.1-assisted instance + semantic labelling of crop plants, weeds and soil in plot images. <a href="https://github.com/appndpird/CropLabel" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>Plot Extractor</h3>
    <p>Geotagged raw-image and orthomosaic crops per plot from Metashape projects or GeoTIFFs, with grid design. <a href="https://github.com/appndpird/plot-extractor" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>PDMA</h3>
    <p>Pawsey Data Management App: rclone-based transfer, sync, sharing and publishing on Acacia object storage. <a href="https://github.com/appndpird/pawsey-uploader" target="_blank" rel="noopener">GitHub</a></p>
  </div>
  <div class="card">
    <h3>PC-Annotate</h3>
    <p>Open annotation tool for large-scale 3D semantic segmentation, with point-cloud registration and volumetric sample generation.</p>
  </div>
  <div class="card">
    <h3>FoSEM</h3>
    <p>LiDAR-based framework for tree stem extraction and modelling (radiata pine plantations).</p>
  </div>
  <div class="card">
    <h3>DotTrack</h3>
    <p>Android video-labelling app for object detection and tracking datasets, with an on-device AI-tracking fork.</p>
  </div>
</div>

## Awards &amp; recognition (selected)

- **Winner of Merit Award, INCITE Awards (Research &amp; Innovation)** — WAITTA, Perth, 2023.
- **Finalist, National iAwards 2023 in Innovation category**, Adelaide, South Australia, 2023
- **Finalist, 31st INCITE Awards (Research &amp; Innovation)** — WAITTA, Perth, 2022.
- **Best Paper Runner-Up — Deep Learning for Earth Observation &amp; Remote Sensing**, DICTA 2021.
- **UWA Convocation Postgraduate Research Travel Award** ($3,000), 2022.
- **Scholarship for International Research Fees (SIRF)** + **PG Top-Up** scholarship (~$10k/yr × 4 yr), UWA, 2019.
- **Two Ad-Hoc Scholarships** (UWA), 2021 &amp; 2023.
- **PSA Fieldwork &amp; Data Collection Awards** (×2), UWA, 2021 &amp; 2022.
- **Best Organiser** — MEGA Challenge national competition, FAST-NUCES, 2015.
- **Bestway Scholarship** for MSc, University of Bradford, UK, 2009.

## Service to the discipline

- Reviewer for *IEEE T-ITS*, *Remote Sensing*, *IEEE Access*, PAMI, ICRA, IROS, IGARSS, DICTA.
- Volunteer, **Women in Data Science (WiDS)** Perth, 2023.
- Active member of the **Australian Plant Phenomics Network** community.
- Adjunct supervisor for HDR students at UWA.
