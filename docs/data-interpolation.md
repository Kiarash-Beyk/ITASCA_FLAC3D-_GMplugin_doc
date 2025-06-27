The following functions should be used to interpolate offset well logs imported into model. Two methods are 
available: Kriging and Inverse Distance Weighted (IDW) method. The former is performed externally using Python 
scripts (see Appendix 1), using the offset well logs and FLAC3D mesh, already prepared and processed using the 
previous functions and exported using the following functions. The latter is performed internally using the 
respective functions described in this section.

Kriging-related functions:

 **:material-rhombus-split: export_importedLog_allWells**: exports well logs for kriging operation for all wells existing in "Wells" List  

Note:  
>This is the main function to be used for log preparation and export for kriging 
Argument: None 

:material-rhombus-split: export_zoneData_perFormation(formationName): exports FLAC3D mesh data for kriging 

Note: 
>This function APPENDS (not overwrites) to "Output/F3D_Zone_IDs.csv" after each call. Must be executed 
for each formation in the model separately

Argument: 

1. formation name (must exist in 'Horizons' List)  

**:material-rhombus-split: import_krigging_parameter**(fileName,log_parameter): imports kriging data (Kriging is performed by 
Python code out of FLAC3D – refer to Appendix I) and saves interpolated values on zone extras 
corresponding to log parameters  

Note: 
>Must be called for each log parameter separately.  

Argument: 

1. File Name - must exist in "Input/" folder. Contents must follow this format: zoneID, attribute (log 
parameter) saved as csv file 
2. Log Parameter - must exist in "Logs" list 

IDW-Related Functions  


**:material-rhombus-split: zone_log_interpolator**(formation,log_pick_method,iwdExp,user_defined_sr): function to interpolate log 
data on mesh using IDW method 

Note:  
>It operates on all log parameters existing in “Logs” list 

Argument: 

1. name of formation on which data is populated. The formation name must exist in "Horizons" list (and 
on slot "Geology") 
2. log smoothing method: enter "1" for smoothing (on "user_defined_sr" interval in relative depth sense 
0-1), "2" for not smoothing (interpolation using unsmoothed original log) 
3. IDW exponent ranging from 1-3. use higher value for more weight on proximity to wells (will result in 
less smooth and patchy interpolation. Use higher values where there is a good number of wells 
distributed throughout the model) 
4. log smoothing interval in relative depth sense. If entered '0' model will calculate smoothing interval 
based on average zone height in formation and interpolation will run slower 

 **:material-rhombus-split: zone_log_interpolator_oneParameter**(formation,log,log_pick_method,iwdExp,user_defined_sr):function to interpolate log data on numerical mesh using IDW method  

Note: 
>Similar to previous function but works on just one log parameter 

Argument: 

1. name of formation on which data is populated. Formation name must exist on "Horizons" map on slot 
"Geology" 
2. log data to be interpolated in model. log property must exist in "Logs" List 
3. log smoothing method: enter "1" for smoothing (on "user_defined_sr" interval in relative depth sense 
0-1), "2" for not smoothing (interpolation using unsmoothed original log) 
4. IDW exponent ranging from 1-3. use higher value for more weight on proximity to wells (will result in 
less smooth and patchy interpolation. Use higher values where there is a good number of wells 
distributed throughout the model) 
5. log smoothing interval in relative depth sense. If entered '0' model will calculate smoothing interval 
based on average zone height in formation and interpolation will run slower 

Constant value assignment 


**:material-rhombus-split: log_assign_zone**(formation,log,value): Function to assign a constant log value to a formation 
(automatically assigned corresponding to that log parameter) 

Note:  
>This function is usually used for shallow formations where no log exists 
Assigns log value to a FLAC3D zone extra memory corresponding to log parameters already set in model 
by “Logs” list 

Argument: 

1. formation name: must exist in model on "Geology" slot (in "Horizons" map) 
2. log parameter name: must exist in imported well logs (in "Logs" map) 
3. user defined log value to be stored in zone extra 
Data Control and Inquiry Functions. These functions can be used to assess, visualize and make inquiries after data 
population  

**:material-rhombus-split: plot_F3D_log**(well,log_para): function to plot interpolated log value in model along an existing offset well 

Note:  
>- At least one valid log must have been imported for the given well for the function to operate 
>- Use "Plot Table" FLAC3D command to see the results. x-axis is TVDSS, y-axis is log value 

Argument:

1. well name: must exist in "Wells" list 
2. log parameter name: must exist in "Logs" list


**:material-rhombus-split: plot_F3D_log_rDepth**(formation,well,log_para): function to plot interpolated log value in model along a 
well for a given formation.  

Note:  
> Use "Plot Table" FLAC3D command to see the results. x-axis is relative depth, ranging from 0 (formation 
top) to 1 (formation bottom), y-axis is log value

Argument :

1. Formation name: must exist in "Horizons" List  
2. Well name: must exist in "Wells" List 
3. Log name: must exist in "Logs" List 

**:material-rhombus-split: export_log_histogram**(log,min,max,bin_cnt): Function to export histogram of a given interpolated log 
parameter in all formations 

Note: 
> - Values are from FLAC3D zones assigned by interpolation and saved on zone extra memory number 
corresponding to the log parameter 
>- exports to "Output/Histogram_log.csv". both frequency and percentage are exported 

Argument:

1. Log name: must exist in "Logs" list and populated on mesh 
2. minimum value 
3. maximum value 
4. no of bins for histogram (max-min divider)  

**:material-rhombus-split: export_log_histogram_formation**(formation,log,min,max,bin_cnt): Function to export histogram of a 
given interpolated log parameter in a given one formation 

Note: 
> - Values are from FLAC3D zones assigned by interpolation and saved on zone extra memory number 
corresponding to the log parameter 
> - exports to "Output/ Histogram_formation_log.csv". both frequency and percentage are exported 

Argument:

1. Formation name: must exist in "Horizons" List  
2. Log name: must exist in "Logs" list and populated on mesh 
3. minimum value 
4. maximum value 
5. no of bins for histogram (max-min divider) 



**:material-rhombus-split: geometry_maker**(top,bot,rDepth): Function to make a surface passing through a formation 

Note: 
>- This function creates a surface passing through a given formation, and conforming formation geometry 
based on upper and lower horizon surfaces.  
>- The created surface is used for the visualization of a parameter in the model, such as a log parameter. 
A given parameter can be projected (painted) on the created surface 
>- Creates a surface named: top@rDepth% 

Argument: 

1. name of target formation - must be similar to model formation names in “Horizons” list 
2. name of immediate bottom formation - must be similar to model formation names in “Horizons” list 
3. relative depth from top of target formation in % ranging 0-100 (entering 50 creates a surface passing 
through the middle of the target formation) 

**:material-rhombus-split: geometry_remover**(name): Function to remove a geometry  

Note: 
>mainly used to remove a geometry surface created by "geometry_maker" function  

Argument: 

1. geometry name  

**:material-rhombus-split: export_F3D_logs_forAddedWell**(well,depthInterval): Function to export ALL interpolated logs as per 
"Logs" list for a non-offset well 

Note :
> - This function operates on a well added to model using "add_well" function. These wells are not 
considered as offset wells and are not included data interpolation. An important application of this 
function is planned well analysis for well design 
>- It exports from interpolated data stored at FLAC3D zone centers (on extra memories corresponding to 
imported logs on “Logs” list )

Argument:

1. Well name: must exist in " added_Wells " List 
2. Depth interval (sampling interval) for log plot/export


**:material-rhombus-split: export_F3D_logs_forOriginalWell**(well,depthInterval): Function to export ALL interpolated logs as per 
"Logs" list for an offset well (existing on “Wells” list) 

Note :
> - This function exports from interpolated data stored at FLAC3D zone centers (on extra memories 
corresponding to imported logs on “Logs” list )

Argument:

1. Well name: must exist in " Wells " List 
2. Depth interval (sampling interval) for log plot/export