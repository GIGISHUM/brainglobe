# BrainGlobe

## Overview
All BrainGlobe tools (e.g., brainreg, cellfinder, brainrender, etc) are napari plugins. <br/>

**Short version**: Raw 3D images are imported in napari → You select an atlas to register it on your sample → You detect cell and get cell coordinates in 3D → You visualize it and create cool animations <br/>

**Long version**: You obtain high-resolution, volumetric data of a sample brain using techniques like BrainSaw, two-photon serial tomography, whole-brain light sheet microscopy, etc → You select an appropriate atlas, at an appropriate age, at an appropriate resolution for it (e.g., Allen Adult Mouse Brain Atlas 25µm) → It does some fancy linear affine transformation then non-linear B-spine transformation → Ultimately the atlas template brain is transformed to your sample brain (and or vice versa) and generates deformation matrices which tells exactly how template and sample spaces should morph to match → You load both raw 3D volumes of the signal and background channels for cell detection → It does some fancy candidate detection algorithm with a 2D filter, then a 3D filter, then some structural splitting → Ultimately you get two layers of 3D coordinates of detected and rejected cells → These two output (transformation and cell coordinates) are combined together to create cool animations

## Official documentation
`BrainGlobe` [Documentation](https://brainglobe.info/index.html) <br/>
`brainreg` [Documentation](https://brainglobe.info/documentation/brainreg/index.html) <br/>
`cellfinder` [Documentation](https://brainglobe.info/documentation/cellfinder/index.html) <br/>
`brainrender` [Documentation](https://brainglobe.info/documentation/brainrender/index.html) <br/>

## Installation
Create virtual environment called brainglobe: <br/>
`conda create -c conda-forge --name brainglobe python=3.12`<br/>

Install napari: <br/>
`conda install -c conda-forge napari pyqt6`<br/>

Install BrainGlobe core packages: <br/>
`pip install brainglobe`<br/>

Install brainreg: <br/>
`conda install -c conda-forge brainreg` (for Mac users) <br/>
`conda install -c conda-forge niftyreg` (for Mac users) <br/>

Install cellfinder: <br/>
`pip install cellfinder[napari]`<br/>

Install brainrender: <br/>
`conda install -c conda-forge ffmpeg` <br/>
`conda install -c conda-forge pyside2` <br/>
`conda install -c conda-forge hdf5` (for Mac users) <br/>
`pip install brainrender`<br/>


## Add virtual environment to Jupyter Notebook
`conda activate brainglobe`<br/>
`pip install ipykernel`<br/>
`python -m ipykernel install --user --name=brainglobe`<br/>

## Workflow
`brainreg` → `cellfinder` → `brainmapper` (napari widget) → `brainrender`, OR <br/>
`brainmapper` (one-line command line tool) → `brainrender`


