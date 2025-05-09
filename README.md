# BCSalmonData
The complete datasets are in the ***source_data/*** subdirectory:
- ***all_wild_sample_events.csv***: wild sampling events from all sources
- ***all_wild_fish_lice.csv***: information from fish caught from those events, including lice counts
- ***industry_farm_details.csv***: information about salmon farms owned by MOWI, Cermaq, and Grieg
- ***industry_farm_abundances.csv***: lice count data on salmon farms collected by salmon farming companies. 
Linked to ***industry_farm_details.csv***
- ***DFO_farm_abundances.csv***: lice count data on salmon farms reported to Fisheries and Oceans Canada (DFO).
Linked to ***industry_farm_details.csv***

The code:
1. Processes and integrates sampling data from a variety of sources to produce the above datasets of farmed and wild salmon 
in British Columbia, Canada
2. Uses the above datasets to generate figures and tables exploring the dataset. The 
figures and tables are used in the publication "Sea lice infestation dataset for wild and farmed salmon populations on 
the Pacific coast of Canada (2001-2023)" by Crawford W. Revie, Thitiwan Patanasatienkul, Gregor McEwan, and Lance 
Stewardson.

## Technical Requirements to run the scripts
1. Python. We used Python 3.9. Any later version should also work.
2. Setup to run Jupyter Notebooks: https://jupyter.org
3. [Pandas](https://pandas.pydata.org). We used version 1.4.2.
4. [Seaborn](https://seaborn.pydata.org/). We used version 0.11.2.

## How to use the data and notebooks to generate the output
Download and extract this project using the "Download ZIP" option in the dropdown from the green button at the top 
of the GitHub page.

### Wild Sampling Data
The wild data set includes sampling information from Fisheries and Oceans Canada (DFO), 
Mainstream Biological Consulting (MBC), Broughton Archipelago Monitoring Plan (BAMP), 
Marine Environmental Research Program (MERP), Marty Krkosek, Pacificus Biological Services, and Kitasoo First Nation.
This data is in ***wild_sample_events.csv*** and ***wild_fish_lice.csv*** in the source_data/ subdirectory.

We have also included data from:
- [Salmon Coast Society](https://salmoncoast.org/research/our-projects/sea-lice-monitoring/)
  ([data](https://github.com/salmoncoast/Sea-lice-database) downloaded 13 Nov 2024)
- [Cedar Coast Society](https://cedarcoastsociety.org) 
([data](https://github.com/CedarCoastFieldStation/Sea-lice-database) downloaded 13 Mar 2025)
- [Hakai Institute](https://catalogue.hakai.org/dataset/ca-cioos_6c449900-c726-4e9a-b241-707711e253a7)
  ([data](https://github.com/HakaiInstitute/jsp-data) downloaded 12 Mar 2025)

The parts of these datasets that we used are included in this repository.

To create data files in our format from these sources, run the following (note we include the interim files produced by
these notebooks):
- Running the Jupyter Notebook ***source_data/Format_SalmonCoast.ipynb*** will use the Salmon Coast Society downloaded 
data to create ***salmon_coast_wild_sample.csv*** and ***salmon_coast_wild_fish_lice.csv***
- Running the Jupyter Notebook ***source_data/Format_CedarCoast.ipynb*** will use the Cedar Coast Society downloaded 
data to create ***cedar_coast_wild_sample.csv*** and ***cedar_coast_wild_fish_lice.csv***
- Running the Jupyter Notebook ***source_data/Format_Hakai.ipynb*** will use the Hakai Institute downloaded 
data to create ***hakai_wild_sample.csv*** and ***hakai_wild_fish_lice.csv***

Running ***source_data/Integrate_Wild_Data.ipynb*** will join all the wild data files together and create 
***all_wild_sample_events.csv*** and ***all_wild_fish_lice.csv***, which are used by the notebooks to create the 
tables and figures.

### Farm Sampling Data

### Generating the Output


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
***Fig1_panels.ipynb*** on the image.