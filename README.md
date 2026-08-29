# SIH2026
## Problem Statement ID: 26175
## Problem Statement: DepthWizard - Single-View Height Estimation and 3D Flythrough
### 🗄️ Recommended Dataset: GAMUS
To train, test, and validate the monocular depth-estimation backbone for this pipeline, the GAMUS Dataset is the recommended open-source foundation. It provides the essential paired data required to translate 2D satellite imagery into accurate depth models.
 * Dataset Name: GAMUS
 * Provider: Earthflow
 * Platform: Hugging Face
 * Access Link: https://huggingface.co/datasets/earthflow/GAMUS

**A lower-resolution DEM source such as SRTM 30 m may be used to map scale-agnostic depth features to absolute metric elevations.**

**NOTE** -> While GAMUS is recommended, you are free to utilize any open-source dataset containing remote-sensing depth data, provided it supports both relative depth training and metric scale calibration.
> Dataset Application Strategy:
> Use this data to overcome the domain gap between natural egocentric imagery (what most foundational models are trained on) and top-down remote sensing imagery. The dataset will be critical for training your model to handle structural variations across urban, sparse, hilly, and forested landscapes.
> 
### 📖 Background
Accurate Digital Elevation Models (DEMs) and Digital Surface Models (DSMs) are fundamental to urban planning, disaster management, and military reconnaissance. Traditional elevation data acquisition methods—such as stereo-imaging pairs, LiDAR, or Interferometric Synthetic Aperture Radar (InSAR)—are often cost-prohibitive, computationally intensive, and dependent on specific sensors.
Single-view height estimation offers an agile alternative. However, current foundational monocular depth models predict relative depth and struggle with remote sensing applications due to domain gaps and a lack of absolute-scale mapping. Converting this relative depth into metric elevation, and transforming those profiles into interactive 3D flythrough assets, remains the primary challenge.
### ⚙️ System Pipeline Description
Develop an end-to-end software pipeline that transforms single-view optical RGB remote-sensing images into high-precision elevation maps. The system must adapt based on the metadata of the uploaded imagery:
 * Non-Georeferenced RGB Imagery (PNG, JPG): Produce a Relative Digital Surface Model (rDSM) for images without spatial metadata, using relative height directly in the visualization stage.
 * Georeferenced RGB Imagery (GeoTIFF): Produce an Absolute Digital Surface Model (DSM) with metric height values. Use a lower-resolution DEM source (e.g., SRTM) or limited Ground Control Points to map scale-agnostic depth features to absolute metric elevations.
3D Rendering & Visualization:
After computing the elevation map, project the original optical image onto the generated 3D terrain mesh. Integrate this with a robust rendering engine (such as Unity, Three.js, or Babylon.js) to support seamless first-person navigation, structural height analysis, and slope assessment from arbitrary aerial perspectives.
### 🎯 Key Milestones
 * Elevation Extraction: Deploy a robust pre-trained monocular depth model to extract geometric and structural representations from single-view optical imagery.
 * Scale Calibration: Build a conversion module to map relative depth to absolute height using scene-level statistics, low-resolution DEMs, semantic priors, or minimal Ground Control Points.
 * Visualization Layer: Create an immersive, interactive rendering pipeline that converts the optical texture and depth map into a navigable 3D environment deployable as a standalone application.
### 📊 Evaluation Criteria
| Category | Weight | Key Metrics & Focus Areas |
|---|---|---|
| DSM Estimation Accuracy | 50% | RMSE, MAE, and correlation against LiDAR/reference data. Must demonstrate performance stability across urban, sparse, hilly, and forested landscapes. |
| Rendering & UX | 50% | Projection accuracy, visual fidelity, 3D flythrough navigability, interface intuitiveness, software stability, and successful standalone deployment. |
### 📦 Expected Solution Deliverables
Deliver a fully integrated software suite, including complete source code and technical documentation. The module must contain two core components:
 * Elevation Estimation Module: Accepts single-view optical satellite imagery (PNG, JPG, or TIFF) and outputs a high-fidelity DSM in a standard geospatial format.
 * Interactive Visualization Platform: A user-friendly interface that allows users to upload imagery, seamlessly fly through the reconstructed 3D terrain, and validate estimated structural heights against reference datasets.
