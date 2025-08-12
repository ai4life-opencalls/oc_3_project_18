 <a href="https://ai4life.eurobioimaging.eu/open-calls/">
    <img src="https://github.com/ai4life-opencalls/.github/blob/main/AI4Life_banner_giraffe_nodes_OC.png?raw=true" width="70%">
  </a>
</p>



# Project #18: Detection of Nuclear Pore Complexes by DNA PAINT

This repository contains code for the automatic detection of Nuclear Pore Complexes (NPC) in localization microscopy. Developed as part of the [AI4Life project](https://ai4life.eurobioimaging.eu), it uses data provided by Emilie Costes from the CBS, Montpellier, FR.
All images used in this tutorial are licensed under **CC-BY**. If any of the instructions are not working, please [open an issue](https://github.com/ai4life-opencalls/oc_3_project_18/issues) or contact us at [ai4life@fht.org](ai4life@fht.org)!

## Introduction
The project focuses on ...



## Installation

Install the [conda](https://conda.io) package, dependency and environment manager.

You can download this repository from the green `Code` button → download ZIP, or clone through the command line with

    cd <path to any folder of choice>
    git clone https://github.com/BIIFSweden/AI4Life_OC3_18.git

Then create the `AI4Life_OC3_18` conda environment:

    cd <path to your 'AI4Life_OC3_18' directory>
    conda env create -f environment.yml

This will install all necessary project dependencies.

## Usage

Copy all project data to the [data](data) directory (or use symbolic links).

Then run [Jupyter Lab](https://jupyter.org) from within the `AI4Life_OC3_18` conda environment:

    cd <path to your 'AI4Life_OC3_18' directory>
    conda activate AI4Life_OC3_18
    jupyter-lab

Inside the `notebooks` folder you will find Jupyter notebooks for:

## Acknowledgements
AI4Life has received funding from the European Union’s Horizon Europe research and innovation programme under grant agreement number 101057970. Views and opinions expressed are however those of the author(s) only and do not necessarily reflect those of the European Union or the European Research Council Executive Agency. Neither the European Union nor the granting authority can be held responsible for them.

## License

[MIT](LICENSE)

Developed by [Kristina Lidayova](mailto:kristina.lidayova@scilifelab.se)
