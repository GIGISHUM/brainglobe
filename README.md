# BrainGlobe

## Overview
All BrainGlobe tools (e.g., brainreg, cellfinder, brainrender, etc) are napari plugins. 

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
`pip install --user ipykernel`<br/>
`python -m ipykernel install --user --name=brainglobe`<br/>

## Using brainreg
brainreg is a tool to map a template atlas to your sample space, and vice versa. 

## Using cellfinder
cellfinder detects the center coordinates of fluorescently labelled cells (bright spots of given size). It _detects_ cells, but does not _segment_ cells. So it allows you to count the number of cells and register the cell coordinates, but it will not create outlines of cells.

cellfinder runs on 3D images (e.g., serial two-photon tomography, whole brain light sheet microscopy, BrainSaw, etc). It needs two channels: **signal** (where your real cells are) and **background** (autofluorescence channel). 

To run cellfinder, you need to know:
* s The primary signal channel: test_brain/ch00.
* -b The secondary autofluorescence channel (or background): test_brain/ch01.
* -o The output directory : test_brain/output.
* --orientation The data orientation: psl.
* -v The voxel spacing in the same order as the data orientation (psl): 5 2 2.
* --atlas The atlas we want to use: allen_mouse_10um.

So, to run cellfinder, go to your designated brainglobe virtual environment, and run in the terminal something like this:
brainmapper -s test_brain/ch00 -b test_brain/ch01 -o test_brain/output -v 5 2 2 --orientation psl --atlas allen_mouse_10um
