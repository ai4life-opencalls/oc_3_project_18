 <a href="https://ai4life.eurobioimaging.eu/open-calls/">
    <img src="https://github.com/ai4life-opencalls/.github/blob/main/AI4Life_banner_giraffe_nodes_OC.png?raw=true" width="70%">
  </a>
</p>



# Project #18: Detection of Nuclear Pore Complexes by DNA PAINT

This repository contains code for the automatic detection of Nuclear Pore Complexes (NPC) in localization microscopy. Developed as part of the [AI4Life project](https://ai4life.eurobioimaging.eu), it uses data provided by Emilie Costes from the CBS, Montpellier, FR.
All images used in this tutorial are licensed under **CC-BY**. If any of the instructions are not working, please [open an issue](https://github.com/ai4life-opencalls/oc_3_project_18/issues) or contact us at [ai4life@fht.org](ai4life@fht.org)!

## Introduction
Nuclear pore complexes (NPCs) are large protein assemblies that regulate the exchange of macromolecules between the nucleus and cytoplasm. In healthy cells, NPCs exhibit a canonical circular or donut‑like architecture with well‑defined diameter, circularity, and stoichiometry. Deviations from this structure are thought to underlie defects in nucleo‑cytoplasmic transport, but they are difficult to quantify systematically at the single‑pore level. This project aims to provide a robust, open pipeline for detecting individual NPCs in DNA‑PAINT data, extracting quantitative shape descriptors, and classifying pores according to their structural deviations.

The data consist of DNA‑PAINT super‑resolution images of Nup107‑labelled NPCs, acquired as localization microscopy movies. The pipeline starts from raw or pre‑localized data (Picasso Localize), performs drift correction and image rendering, and then detects nucleus and segments individual pores within the nucleus. NPC candidates are separated from free proteins, noise, and other structures using a combination of localization‑space clustering, intensity‑based filters, and position constraints relative to the nuclear mask. For each detected NPC, the workflow computes features such as centroid, diameter, circularity, ellipticity (via ellipse fitting), and proxies for stoichiometry based on the number and density of localizations.

## Installation

Install the [conda](https://conda.io) package, dependency and environment manager.

You can download this repository from the green `Code` button → download ZIP, or clone through the command line with

    cd <path to any folder of choice>
    git clone https://github.com/ai4life-opencalls/oc_3_project_18.git

Then create the `oc_3_project_18` conda environment:

    cd <path to your 'oc_3_project_18' directory>
    conda env create -f environment.yml

This will install all necessary project dependencies.

## Usage

Copy all project data to the [data](data) directory (or use symbolic links).

Then run [Jupyter Lab](https://jupyter.org) from within the `oc_3_project_18` conda environment:

    cd <path to your 'oc_3_project_18' directory>
    conda activate oc_3_project_18
    jupyter-lab

Inside the `notebooks` folder you will find Jupyter notebooks for:

### Step 1 : [Preprocessing the localizations](notebooks/1-Preprocess_localizations.ipynb)

This notebook preprocesses single-molecule localization data to make it cleaner and more reliable for downstream analysis. It filters low-quality localizations, corrects sample drift, and then segments the nucleus so that only localizations inside the relevant biological region are kept. This reduces false localizations from background and out-of-focus signals, improving the accuracy of later measurements. The pipeline consists of:

1. Data loading - loads the .hdf5 file together with metadata containing localizations
2. Quality filter - filters the localizations based on reasonable precision and brightness
3. Simple localisation diagnostics - checks temporal stability and spatial uniformity
4. Undrift the localizations -  corrects the localizations for the drift using AIM method
5. Rendering - renders the localizations using Picasso Render and save them as a png image
6. Segment nucleus using morphological operations
7. Spatial filtering - filter the localizations based on their spatial location within nucleus 
8. Saving the processed localizations into .hdf5 and .yaml files, and rendered image into .png file.

<img width="4526" height="1498" alt="image1" src="https://github.com/user-attachments/assets/28d5cdbd-77a1-40af-9775-e4a14582e50c" />

_Figure 1: (left) rendered localisations, (middle) segmented nucleus, (right) nucleus edge in red is overlaid on the localisations._

<img width="1570" height="1453" alt="nucleus_NPC" src="https://github.com/user-attachments/assets/632cd470-13f0-47e6-9edb-dc4161222cbf" />

_Figure 2: Localisations spatially filtered to position within nucleus, zoomed and rendered at higher resolution._

### Step 2 : Detecting Nuclear Pore Complexes (NPC) using Picasso software

<img width="1951" height="1279" alt="Screenshot (183)" src="https://github.com/user-attachments/assets/d8edb0c2-b8de-403b-b7de-4e96d4e062a9" />
_Figure 3: NPCs detected using "Pick similar" function in Picasso software after manual selection of few NPCs._

### Step 3 : [Analazing the detected Nuclear Pore Complexes](notebooks/2-Analyze_NPCs.ipynb)

This notebook focuses on extracting and quantifying nuclear pore complex (NPC) geometry from localization data. It renders the localizations for visual inspection, fits ellipses to each NPC, and calculates feature values so the structure of individual pores and the overall population can be evaluated consistently.
The pipeline consists of:

1. Data loading - loads the .hdf5 file together with metadata containing localizations
2. Render the localizations using Picasso Render, crop the central part and save as a png:
3. Calculate and visualise NPC features and fit ellipse to NPC localisations
4. Visualize fitted on the rendering of NPC localizations
5. Examine features of specific NPC by setting the group_ID variable
6. Statistical summary of distribution of feature values over all the NPC's

<img width="2070" height="1900" alt="npc_ellipses" src="https://github.com/user-attachments/assets/d4614575-99dd-43f3-ba64-b2f9b7316cba" />
_Figure 4: Ellipses fitted to NPCs plotting on top of the localizations rendering._

## Acknowledgements
AI4Life has received funding from the European Union’s Horizon Europe research and innovation programme under grant agreement number 101057970. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.

## License

[MIT](LICENSE)

Developed by [Kristina Lidayova](mailto:kristina.lidayova@scilifelab.se)
