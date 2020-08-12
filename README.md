# Evaluating the relationship between the area and latitude of large igneous provinces and Earth’s long-term climate state

This repository contains data and code associated with the following paper:

Park, Y., Swanson-Hysell, N.L., Macdonald, F.A., Lisiecki, L.E., 2020, (accepted; in press), Evaluating the relationship between the area and latitude of large igneous provinces and Earth’s long-term climate state *Large Igneous Provinces: A Driver of Global Environmental and Biotic Changes. AGU Geophysical Monograph 255*. Preprint available on EarthArXiv: 10.31223/osf.io/p9ndf.

## Computational Environment

Three separate computational environments are required to successfully execute the Jupyter notebooks contained within this repository. The [Repository Overview](#repository-overview) documents which environment is required for each notebook.

### Python 3

Non-standard modules used are:

* cartopy
* netCDF4

These modules can be installed via pip or conda.

The full computational environment used to execute this code can be found within the LIP_python3.yml file in this repository.

### Python 2

A Python 2 kernel is required, since much of the analyses performed in this repository rely heavily on functions within pygplates (http://www.gplates.org/docs/pygplates/index.html). The pygplates code is only compatible with Python 2, which is why this code is in Python 2 rather than 3.

In additional to the pygplates library, other non-standard modules used are:

* cartopy
* shapely
* netCDF4

These modules can be installed via pip or conda.

The full computational environment used to execute this code can be found within the LIP_python2.yml file in this repository.

### Matlab

A Matlab kernel is required to execute one notebook within this repository.

## Repository Overview

### Code

This folder contains the Jupyter notebooks that were used to perform the analyses presented in this study.

* `Correlation_analysis.ipynb`
    * Uses a Matlab kernel to assess the statistical significance of correlation between time series of zonal large igneous province area (i.e. the area of large igneous provinces in a given latitude band) and ice extent.
* `Franklin_Umkondo.ipynb`
    * Uses a Python 2 kernel to calculate the area of the Franklin and Umkondo large igneous provinces in the tropics at the time of their emplacement.
* `Paleogeographic_Reconstruction.ipynb`
    * Uses a Python 2 kernel to reconstruct the paleolatitude and calculate the zonal area (i.e. the area in a given latitude band) of large igneous provinces throughout the Phanerozoic.
    * Outputs of this analysis are stored in the `reconstruction_output` subfolder.
* `Present_Day_Areas.ipynb`
    * Uses a Python 3 kernel to assess the timescale of the progressive erosion of large igneous provinces by comparing estimated original areas (i.e. the area at the time of emplacement) and observed present day areas (i.e. the area preserved today).
* `Tropical_Rain_Belt.ipynb`
    * Uses a Python 3 kernel to visualize modern climatological data and estimate the latitudinal width of the tropical rain belt.
* `recon_tools.py`
    * Contains functions that assist in analysis/visualization of paleogeographic reconstructions.
* `LIP_python2.yml`
    * Contains the full computational environment that was used to execute the Jupyter notebooks that require a Python 2 kernel.
* `LIP_python3.yml`
    * Contains the full computational environment that was used to execute the Jupyter notebooks that require a Python 3 kernel.

### Data

This folder contains the data that are used in the Jupyter notebooks in the `Code` folder.

* `climate`
    * Contains modern climate data used in `Tropical_Rain_Belt.ipynb`.
    * From https://www.esrl.noaa.gov/psd/data/gridded/data.ncep.reanalysis.derived.surfaceflux.html.
        * temperature (`tmp.0-10cm.mon.ltm.nc`)
        * runoff (`runof.sfc.mon.ltm.nc`)
        * precipitation (`prate.sfc.mon.ltm.nc`)
        * potential evaporation (`pevpr.sfc.mon.ltm.nc`)
        * land mask (`lsmask.19294.nc`)
    * Evaporation minus precipitation data (`ERAI.EP.1979-2015.nc`) were taken from https://climatedataguide.ucar.edu/climate-data/era-interim-derived-components.
        * Note that the the raw netCDF file (ERAI.EP.1979-2015.nc) was too large to be uploaded to GitHub - we therefore calculate the mean (with respect to time) for each pixel and create a new netCDF file that contains only this mean data, and include this smaller netCDF file within this GitHub repository.
    * Another temperature data file (`temp1x1.nc`) is from https://crudata.uea.ac.uk/~timm/grid/CRU_TS_2_1.html.
    * Another runoff data file (`runoff1x1.nc`) is from http://www.grdc.sr.unh.edu/.
* `evaporites`
    * Contains evaporite data (location and age) used in `Paleogeographic_Reconstruction.ipynb`.
* `LIPs`
    * Contains the LIP outline shapefiles used in `Paleogeographic_Reconstruction.ipynb` and `Franklin_Umkondo.ipynb`, modified slightly from Ernst and Youbi (2017) and Ernst et al., Chapter 1 this volume, to ensure that all currently exposed volcanic lithologies are encapsulated by the initial LIP surface area polygons.
        * `LIP_Outline_edited.x` contains the initial LIP surface area polygons (shapefile used in analysis).
        * `LIP_Outline_edited_plot_0_520.x` contains the initial LIP surface area polygons for LIPs younger than 520 Ma (for plotting purposes only).
        * `LIP_current_extent_plot_0_520.x` contains the presently exposed LIP surface area polygons for LIPs younger than 520 Ma.
        * `LIP_Outline_edited_plot_520_1300.x` contains the initial LIP surface area polygons for LIPs between 520 and 1300 Ma (for plotting purposes only).
        * `Franklin.x` contains the initial LIP surface area polygon for the Franklin LIP.
        * `Umkondo.x` contains the initial LIP surface area polygon for the Umkondo LIP.
* `pCO2`
    * These files contain the pCO$_{2}$ proxy compilation of Foster et al. (2017), used in `Paleogeographic_Reconstruction.ipynb`.
* `CEED6_POLY.x`
    * These files contain the polygons and associated metadata of polygons (tectonic units) used in the paleogeographic model of Torsvik and Cocks (2016), used in `Paleogeographic_Reconstruction.ipynb`.
* `CEED6_POLY_AREA.csv`
    * Contains the tabulated area of polygons (tectonic units) used in the paleogeographic model of Torsvik and Cocks (2016), used in `Paleogeographic_Reconstruction.ipynb`.
* `HALIP_extent.csv`
    * The observed present day extents of the High Arctic large igneous province, used in `Present_Day_Areas.ipynb`.
* `Ice_Extent.csv`
    * The latitudinal extent of ice from Macdonald et al. (2019).
* `LIP_X.csv`
    * These files contain the area of large igneous province area (both estimated original areas and observed present day areas), used in `Present_Day_Areas.ipynb`.
* `TC2017_SHM2017_D2018.rot`
    * The paleogeographic model (as a rotation file) used in `Paleogeographic_Reconstruction.ipynb`.

### Manuscript

This folder contains the materials used to generate the initially submitted manuscript. Note that the final published version of the manuscript has minor differences to the version of the manuscript included here.

* `Figures`
    * Contains the figures used in the manuscript.
* `gsabull.bst`
    * Lets LaTeX know how to style the references.
* `Manuscript.tex`
    * The LaTeX code used to generate the submitted manuscript.
* `References.bib`
    * A database of references that LaTeX uses to generate citations in the manuscript.
* `Manuscript.pdf`
    * .pdf of the submitted manuscript.
