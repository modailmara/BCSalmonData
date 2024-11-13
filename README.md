# BCSalmonData
This code generates figures and tables exploring a dataset of farmed and wild salmon in British Columbia, Canada. The 
figures and tables are used in the publication "Sea lice infestation dataset for wild and farmed salmon populations on 
the Pacific coast of Canada (2001-2023)" by Crawford W. Revie, Thitiwan Patanasatienkul, Gregor McEwan, and Lance 
Stewardson.

## Technical Requirements to run the scripts
1. Python. We used Python 3.9. Any later version should also work.
2. Setup to run Jupyter Notebooks: https://jupyter.org
3. Pandas https://pandas.pydata.org. We used version 1.4.2.
4. Seaborn https://seaborn.pydata.org/. We used version 0.11.2.

## How to use the data and notebooks to generate the output
1. Download and extract this project using the "Download ZIP" option in the dropdown from the green button at the top 
of the page.
2. Add the source data 
   1. Download the four data files (listed below) from *UNKNOWN* and add them to the directory 
   *BCSalmonData/source_data/* 
      1. *industry_farm_abundance.csv*
      2. *industry_farm_details.csv*
      3. *wild_fish_lice.csv*
      4. *wild_sample_events.csv*
   3. Download the Salmon Coast Field Station sea lice data from https://github.com/salmoncoast/Sea-lice-database
   4. Extract and move the Salmon Coast data so that the files *BroughtonSeaLice_fishData.csv* and 
   *BroughtonSeaLice_siteData.csv* are in the directory *BCSalmopnData/source_data/SalmonCoast/Data/*
3. Integrate the Salmon Coast data into our wild data
   1. Run the Jupyter Notebook *BCSalmonData/source_data/Integrate_SalmonCoast.ipynb*
   2. Two new files should appear in *BCSalmonData/source_data/* - *all_wild_fish_lice.csv* and 
   *all_wild_sample_events.csv*
4. Run Jupyter Notebooks in *BCSalmonData/generate_figures_tables/* to generate figures and tables from the paper. 
Output png and csv files will appear in subdirectories of *BCSalmon/output*

## Comments on the code, data, and output

This code generates PNG images for the figures and CSV files for the tables. Figure PNG files are complete in themselves
and used directly in the paper. Table CSV files were imported into Microsoft Excel for formatting before being added to 
the paper.

### Figure 1 (the annotated map)
There are multiple components to the map figure and much of the work is outside this code. We outline our process here
so readers can see how we used the output from the code.
1. We used QGIS (https://qgis.org) to create a map of the relevant area.
2. We then used the csv files from *Fig1_coordinate_files.ipynb* to create separate layers for the positions of farms
and wild sampling sites.
3. We used polygon layers to draw the coloured boundaries around the sites.
4. We then exported the map image from QGIS, and used GIMP (https://www.gimp.org) to place the PNG panels from 
*Fig1_panels.ipynb* on the image.