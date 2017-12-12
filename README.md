# owf-data-co-watershed-groups #

This repository contains the [Open Water Foundation (OWF)](http://openwaterfoundation.org) dataset for Colorado watershed groups.
This is a foundational dataset that provides unique identifiers and other data for watershed groups.
The identifiers can be used to link other datasets, such as roundtable basins.
OWF has created and is maintaining this dataset to facilitate work on various data analysis and visualization projects in Colorado.

## Repository Contents ##

The repository contains the following:

```text
analysis/                               TSTool software command files to process data into useful forms.
  Process-xlsx-to-csv.TSTool            TSTool command file that processes the core dataset from .xlsx to .csv.
data-orig/                              Folder containing original data files downloaded from agency websites.  
data/                                   Folder containing data files.
  Colorado-Watershed-Groups.xlsx        Simple Excel file containing core data.
  Colorado-Watershed-Groups.csv         The Excel file contents from the WatershedGroup worksheet converted to a csv file, useful for automated processing.
  WatershedGroup-Document-Relate.csv    The Excel file contents from the WatershedGroup_Document_Relate worksheet converted to a csv file, useful for automated processing.
  WatershedGroup-GNIS-Relate.csv        The Excel file contents from the WatershedGroup_GNIS_Relate worksheet converted to a csv file, useful for automated processing. **TO BE ADDED**
  WatershedGroup-HUC8-Relate.csv        The Excel file contents from the WatershedGroup_HUC8_Relate worksheet converted to a csv file, useful for automated processing. **TO BE ADDED**
doc/
  ?                                     Additional documentation for the dataset.
.gitattributes                          Git configuration file indicate repository configuration, in particular handling of line-ending and binary files.
.gitignore                              Git configuration file to ignore files that should not be committed to the repository.
README.md                               Explanation of repository contents, data files and sources and TSTool command files used to process the core data into other products.
```

### Colorado-Watershed-Groups.xlsx Contents ###

The core Excel workbook that serves as the master data contains the following data columns within the **WatershedGroup** worksheet.

* **WatershedGroupName** -- name of the watershed group; from the Colorado Watershed Assembly's [Watershed Group Directory 2017](https://static1.squarespace.com/static/53f664ede4b032c1fade347d/t/59e0f59a03596e4763b51b3d/1507915163576/CWAwatershedgroupdirectory2017.pdf) 
* **OWF_ID** -- unique text identifier created by OWF; see identifier conventions described below
* **GNIS_Name_CSV** -- [Geographic Names Information System](https://geonames.usgs.gov/apex/f?p=138:1:9185633219989) name(s) of the river/creek in which the watershed group works, to link to the [Source Water Route Framework](http://cdss.state.co.us/GIS/Pages/AllGISData.aspx) spatial data layer
* **GNIS_Name_Flag** -- data status of GNIS_Name values; see more detail below
* **GNIS_ID_CSV** -- [Geographic Names Information System](https://geonames.usgs.gov/apex/f?p=138:1:9185633219989) ID(s) of the river/creek in which the watershed group works, to link to the [Source Water Route Framework](http://cdss.state.co.us/GIS/Pages/AllGISData.aspx) spatial data layer
* **GNIS_ID_Flag** -- data status of GNIS_ID values; see more detail below
* **HUC8_CSV** -- 8-digit Hydrologic Unit Code(s) of the basin in which the watershed group works; to link to spatial data layers
* **HUC8_Flag** -- data status of HUC8 values; see more detail below
* **IBCC_Basin** -- [Interbasin Compact Committee (IBCC)](http://cwcb.state.co.us/about-us/about-the-ibcc-brts/Pages/main.aspx) basin in which the watershed group works; from the Colorado Watershed Assembly
* **IBCC_Basin_Flag** -- data status of IBCC_Basin values; see more detail below
* **Website** -- website URL of the watershed group; from the Colorado Watershed Assembly
* **Website_Flag** -- data status of Website values; see more detail below
* **Comment** -- any other information about the watershed group

Column names are taken from original sources if possible.  For clarity and attribution, agency abbreviations may be added to the original column name.  Column name length is not restricted, therefore, some data representations such as Esri shapefiles may contain truncated column names.  In such cases, alternative formats such as GeoJSON are recommended.

Descriptions of data columns are also provided in the **Notes** worksheet within the workbook.  This worksheet also details how the original data were downloaded and where to find those files.

#### Identifier Conventions for OWF_ID ####
The OWF_ID is a unique identifier for watershed groups and has been created because a unique identifier is not available in the original data.  The following conventions are used to create OWF_IDs.
If a watershed group is known by a well-recognized acronym, such as CUSP (Coalition for the Upper South Platte), then that acronym is used.
* All = Alliance
* Cltn = Coalition
* Com = Committee
* Conserv = Conservancy / Conservation
* Coun = Council
* Crk = Creek
* FOT/FO = Friends of the / Friends of
* Grnwy = Greenway
* Grp = Group
* LT = Land Trust
* Mtn = Mountain
* ResCom = Restoration Committee
* ResProj = Restoration Project
* Rvr = River
* TF = Task Force
* Vly = Valley
* W = Watershed
* WA = Watershed Association
* WAuth = Watershed Authority
* WC = Watershed Coalition
* WCoun = Watershed Council
* WFor = Watershed Forum
* WFdn = Watershed Foundation
* WG = Watershed Group
* WI = Watershed Initiative
* WP = Watershed Partnership

#### Data Flags ####
For many data columns, a second column of the same name with the word "_Flag" added to the column name is present.  These columns are an indication of data status as it relates to missing data.  The following conventions are used:
* G = Value is known/good.  
* g = Value is estimated (but good).  The associated cell is also highlighted in yellow. 
* N = Value is not applicable and a blank cell is expected.
* M = Value is known to be missing in original source and therefore a blank cell indicates that a value cannot be provided.
* m = Value is estimated to be missing.  The associated cell is also highlighted in gray.
* z = Value is unable to be confirmed.  A value is possible but cannot be confirmed one way or the other.  The associated cell is also highlighted in orange.
* x = OWF has not made an attempt to populate the cell at this time.  The value is missing because OWF has not attempted to find the value.  The associated cell is also highlighted in black.

*Note that colors are visible only in xlsx files and not csv files.*

Single-character flags may also be followed with a number, as in g1.  These flags are specific to certain columns and are detailed above in the descriptions of the data columns, if appropriate.

Other worksheets within the workbook contain the following:

* **WatershedGroup_GNIS_Relate** worksheet lists the watershed groups that work in more than one watershed or creek and therefore are associated with more than one GNIS Name and GNIS ID.  This worksheet is organized so that each GNIS Name/ID associated with a watershed group is its own record.  Therefore, the same watershed group may be listed in more than one row and be associated with a different GNIS Name/ID.  This will allow for the establishment of one-to-many relationships when linking to and processing other datasets.  **TO BE COMPLETED**

* **WatershedGroup_HUC8_Relate** worksheet lists the watershed groups that work in more than one watershed or creek and therefore are associated with more than one HUC8 watershed.  This worksheet is organized so that each HUC8 watershed associated with a watershed group is its own record.  Therefore, the same watershed group may be listed in more than one row and be associated with a different HUC8 watershed.  This will allow for the establishment of one-to-many relationships when linking to and processing other datasets.  **TO BE COMPLETED**

* **WatershedGroup_Document_Relate** worksheet lists the watershed groups and any associated documents, such as watershed plans.  This worksheet is organized so that each document associated with a watershed group is its own record.  Therefore, the same watershed group may be listed in more than one row and be associated with a different document.  This will allow for the establishment of one-to-many relationships when linking to and processing other datasets.

* **ChangeLog** worksheet indicates any changes made to the dataset, the date they occurred and who made the changes.

* **Metadata_WatershedGroup** worksheet serves as the metadata for data columns in the **WatershedGroup** worksheet. 


### Colorado-Watershed-Groups.csv Contents ###

This file is the **WatershedGroup** worksheet saved in csv format.  Warning:  if this file is opened directly in Excel, IDs that contain leading zeroes will not show those zeroes.  Instead, import the file into a blank Excel file by selecting Data/Get External Data/From Text.

### WatershedGroup-GNIS-Relate.csv Contents **NOT YET ADDED** ###

This file is the **WatershedGroup_GNIS_Relate** worksheet saved in csv format.  Warning:  if this file is opened directly in Excel, IDs that contain leading zeroes will not show those zeroes.  Instead, import the file into a blank Excel file by selecting Data/Get External Data/From Text.

### WatershedGroup-HUC8-Relate.csv Contents **NOT YET ADDED** ###

This file is the **WatershedGroup_HUC8_Relate** worksheet saved in csv format.  Warning:  if this file is opened directly in Excel, IDs that contain leading zeroes will not show those zeroes.  Instead, import the file into a blank Excel file by selecting Data/Get External Data/From Text.

### WatershedGroup-Document-Relate.csv Contents ###

This file is the **WatershedGroup_Document_Relate** worksheet saved in csv format.  Warning:  if this file is opened directly in Excel, IDs that contain leading zeroes will not show those zeroes.  Instead, import the file into a blank Excel file by selecting Data/Get External Data/From Text.


## Attribution ##

The data sources for this dataset are listed below.

* The Colorado Watershed Assembly's [Watershed Group Directory 2017](https://static1.squarespace.com/static/53f664ede4b032c1fade347d/t/59e0f59a03596e4763b51b3d/1507915163576/CWAwatershedgroupdirectory2017.pdf) provided the list of watershed groups and is the source of the data columns WatershedGroupName, IBCC_Basin_CSV and Website.  See the Data Workflow section below to learn how the dataset was initially created.
* The U.S. Geological Survey (USGS)'s [Geographic Names Information System (GNIS)](https://geonames.usgs.gov/apex/f?p=138:1:9185633219989) is the Federal and national standard for geographic nomenclature.  The USGS developed the GNIS in support of the U.S. Board on Geographic Names as the official repository of domestic geographic names data.
The GNIS ID is provided in the Source Water Route Framework (SWRF) spatial data layer provided by [Colorado's Decision Support Systems](http://cdss.state.co.us/GIS/Pages/AllGISData.aspx).  To find the GNIS ID and Name associated with a watershed group, the SWRF layer was opened in QGIS and manually cross-referenced the watershed/river described in a watershed group's website with the watershed/river's name (GNIS_Name) in the SWRF.
Because there are several creeks with the same GNIS Name (i.e., Bear Creek), it was often necessary to select all creeks with the same GNIS Name to find the one in the correct location. 
* HUC8 data come from a [prototype visualization](http://viz.openwaterfoundation.org/co/cwcb-viz-co-watershed-plans/index.html) created by OWF.  OWF received data from the Colorado Water Conservation Board in May 2017 regarding 8-digit Hydrologic Unit Code (HUC) basins and associated watershed plans.  Included with this data was a data field titled "Organization".  OWF manually cross-referenced Organization with WatershedGroupName to get HUC8 data for many of the watershed groups.  The data were also available as a GeoJSON spatial layer.  OWF overlayed this layer with the SWRF layer to find the HUC8 for watershed groups that did not have watershed plan data associated with them.  Links to watershed plans were provided and can be found in the **WatershedGroup_Document_Relate** worksheet in the Website column.
* OWF_ID was created for each watershed group by OWF in order to ensure that at least one type of identifier contains values for every watershed group.  The OWF_ID is needed to potentially link every watershed group to other datasets.  OWF_ID is used in "Relate" worksheets and csv files as the identifier for this reason.  


## Data Workflow ##

This dataset was previously created by OWF during work developing a statewide list of contacts for watershed groups.  OWF compiled the list of watershed groups from the Colorado Watershed Assembly's [2014 Watershed Group Directory](https://coloradowater.charityfinders.com/images/watershed%20group%20directory%2008_07_2014.pdf).  
OWF took this initial dataset and cross-referenced it with the [Watershed Group Directory 2017](https://static1.squarespace.com/static/53f664ede4b032c1fade347d/t/59e0f59a03596e4763b51b3d/1507915163576/CWAwatershedgroupdirectory2017.pdf) as provided by the [Colorado Watershed Assembly](http://www.coloradowater.org/).  Any group that had been on the 2014 list but not the 2017 list (e.g., the Coalition for the Poudre River Watershed) was searched for online.  If the group is still in operation then it is listed in the dataset. 
The 2017 directory lists watershed groups according to Interbasin Compact Committee (IBCC) basin and provides website URLs for groups, if available.  From here, the general workflow is as follows:
1. Data flags are created for many of the data columns that indicate data status as described above.
2. The data are formatted as a table to allow for data filtering.
3. The dataset is saved in .xlsx format.
4. The xlsx-formatted file is opened in TSTool and a short command file [(Process-xlsx-to-csv.TSTool)](https://github.com/OpenWaterFoundation/owf-data-co-watershed-groups/blob/master/analysis/Process-xlsx-to-csv.TSTool) converts the dataset into CSV format.
5. The xlsx-formatted file is opened in TSTool and a short command file converts the dataset into GeoJSON format.  This step is optional and applicable for datasets in which a map will be created or if further processing will occur in GIS application such as QGIS.  **This step will be implemented in the future.**

## How to Use the Data ##

The Colorado Watershed Groups dataset provides a statewide list of watershed groups.  There is a unique identifier for each watershed group (more may be added in the future) and the dataset allows for cross-referencing the identifier
so that other datasets can be joined.  For example, the [Colorado Roundtable Basins dataset](https://www.github.com/OpenWaterFoundation/owf-data-co-roundtable-basins) can potentially be used to link additional data.  It is envisioned that enhancements to the dataset will include the addition of environmental data, such as instream flows or preferred habitat for fish.

The Excel and csv files can be used as tabular datasets as is, to create filtered lists or to link to other datasets.  Data-processing software such as TSTool can be used to link this dataset to other datasets.  Datasets can be used within GIS software to create maps.

The format and contents of the dataset will change over time.  It is recommended to save a copy of the dataset for local processing or to fix the version in time.

## Disclaimer ##

OWF has created a statewide dataset of watershed groups.  OWF will attempt to fill data gaps as the dataset is used for analysis and funding allows for more data review.  OWF provides no guarantee as to the accuracy of the data.  **Use this dataset at your own risk.**  OWF welcomes feedback to improve the dataset.

## License ##

The license is being determined.  All the data are public so there are not really any restrictions on use.

## Contributing ##

The Open Water Foundation is adding value by cross-referencing datasets.
If you use the dataset and have comments, please contact the maintainers and/or use the GitHub issues to provide feedback.

## Maintainers ##

Kristin Swaim (@kswaim, kristin.swaim@openwaterfoundation.org) is the primary maintainer at the Open Water Foundation.

Steve Malers (@smalers, steve.malers@openwaterfoundation.org) is the secondary contact.

## Contributors ##

None yet, other than OWF staff.
