Functions in this section can be used to visualize, make inquires and export data from model. Their operation has 
no effect on model results and state.  

**:material-rhombus-split: export_WellPicks_AllWells**: function to export well picks in TVDSS for all offset wells in model. 

Note: 
>- Operates just on offset wells imported by "Import_Wells" function and well name must exist in “Wells” 
list 
>- Returns 9999 if fails to find a well-to-horizon intersection (no well trajectory, no horizon, no intersection) 
>- Export results to "Output/F3D_FormationTops.csv". Overrides if file already exists. 

Argument: None 

:material-rhombus-split: export_WellPicks_OneWell(wellName): function to export well picks (TVDSS) for a given well 

Note : 
> - Operates on offset and non-offset wells imported by "Import_Wells" and “add_well“ functions  
> - Returns 9999 if fails to find a well-to-horizon intersection (no well trajectory, no horizon, no intersection) 
> - Export results to "Output/F3D_FormationTops_wellName.csv". Overrides if file already exists 

Argument:

1. Well name: must exist in either “Wells” or “added_Wells” list 

**:material-rhombus-split: export_F3D_ZoneExtra_MD**(wellName,extra,depthInterval,name): Function to export a zone extra 
parameter  

Note: 
> - Operates on offset and non-offset wells imported by "Import_Wells" and “add_well“ functions  
> - Exports to file "F3D_Export_extrax_wellName_MD.csv" stored in "Output/" folder. Overrides if file 
already exists 

Argument:

1. Well name: must exist in either “Wells” or “added_Wells” list 
2. zone extra number from which data is exported 
3. export sampling (data) depth interval (MD) 
4. User-defined name for exported parameter - is added to header of exported file 

**:material-rhombus-split: export_F3D_ZoneExtra_allWells_MD**(extra,depthInterval): Function to export a zone extra parameter for 
all wells existing in model 

Note: 
>- Operates on offset and non-offset wells imported by "Import_Wells" and “add_well“ functions  
- Exports to separate files "F3D_Export_extrax_wellName_MD.csv" stored in "Output/" folder. Overrides 
if file already exists 
Argument: 
1. zone extra number from which data is exported 
3. export sampling (data) depth interval (MD) 

**:material-rhombus-split: plot_zone_extra**(well,zextra,name,depthInterval): Function to plot a zone extra along a well in model in 
TVDSS 

Note: 
>Operates on offset and non-offset wells imported by "Import_Wells" and “add_well“ functions  
Use “Plot Table” FLAC3D command to see the output. X-axis is TVDSS, y-axis is data numeric value 

Argument:

1. Well name: must exist in either “Wells” or “added_Wells” list 
2. zone extra number (integer)  
3. User-defined name for extracted parameter (is used for plot legend) 
4. depth interval for sampling 

**:material-rhombus-split: plot_zone_extra_remove**(well,zextra): function to delete generated plot by “plot_zone_extra” function 

Note: 
>Use to avoid generating too many plots 

Argument:

1. Well name: must exist in either “Wells” or “added_Wells” list 
2. zone extra number (integer) 