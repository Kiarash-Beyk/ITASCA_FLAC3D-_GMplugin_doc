The following functions operate on offset well logs: importing, processing, visualizing 

**:material-rhombus-split: Well_log_import_all**: Function to import logs for all wells already added to model by "Import_Wells".  

Note: 

>- A well trajectory must exist for all wells for which logs are imported. Any log data point falling out of 
well trajectory coverage is ignored and not imported.  
>- Consistent with general depth convention, all depths in logs must be TVDSS reported in neg number for 
below MSL 
>- Function reads csv logs stored in "FLAC3D/Log/” folder. The “csv” logs must have the names exactly 
similar to the well name imported already by "Import_Wells” function. 
>- Name of log parameters ( such as DTC, DTS, etc.) are read from column header in “well_name.csv” and 
are registered in the “Logs” list  
>- The log list can be printed by: “fish list contents Logs”.  
>- Log parameter names and order must be consistent for all wells. 

**Argument**: None

The following functions are auxiliary functions for QC/QA of imported log 

**:material-rhombus-split: log_coverage_one_parameter**(log_para_name): Function to export log coverage for all formations and 
all offset wells in model. It exports log coverage for each formation in percentage.  
Note:  
> - Exports to "Output/Log_Coverage_log_para.csv" 

Argument:  

1. inquiry log parameter (such as DTC – must exists in the Logs list (imported by "Well_log_import_all") )

**:material-rhombus-split: log_coverage_well**(well): Function to export log coverage (all logs in "Logs" list) along a given offset well 
imported in model.  

Note:  
> -It exports log coverage for each formation in %. Exports to "Output/Log_Coverage_well.csv"


Argument:  

1. inquiry well name. Must exist in "Wells" table (imported by "Import_Wells") 

 **:material-rhombus-split: plot_smoothed_log_rDepth**(formation,well,log,log_pick_method,user_defined_sr): Function to visualize 
log smoothing operation results. 

Note:  
> This function does not change the original log but shows how user selected smoothing method operates 
on a given log. It is recommended to use smoothed logs for log interpolation to remove noises. In order 
to see the result, use plot "Table" command: x-axis is relative depth, ranging from 0 (formation top) to 1 
(formation bottom), y-axis log value 


Argument:  

1. formation name. Must exist in "Horizons" list (on slot "Geology") 
2. well name. Must exist in "Wells" list 
3. log name. Must exist in "Logs" list.  
4. log smoothing method: enter "1" to enforce smoothing (on "user_defined_sr" depth interval) or , "2” 
to avoid smoothing.  
5. smoothing interval in relative depth, ranges 0 to 1. Higher number more smoothing. Selecting “1” 
results in including all log data points in the given formation, for smoothing operation at each point 



**:material-rhombus-split: plot_imported_log_rDepth**(formation,well,log_para): function to plot a given imported log, for a given 
well in a given formation, in relative depth format. 

Note: 
 
> Use the command “Plot Table” to see the log. x-axis is relative depth, ranging from 0 (formation top) to 
1 (formation bottom), y-axis log value 

Argument:

1. formation name. Must exist in "Horizons" list (on slot "Geology") 
2. well name. Must exist in "Wells" list 
3. log name. Must exist in "Logs" list
4. log smoothing method: enter "1" to enforce smoothing (on "user_defined_sr" depth interval) or , "2” 
to avoid smoothing.  
5. smoothing interval in relative depth, ranges 0 to 1. Higher number more smoothing. Selecting “1” 
results in including all log data points in the given formation, for smoothing operation at each point 

**:material-rhombus-split: plot_imported_log_rDepth**(formation,well,log_para): function to plot a given imported log, for a given 
well in a given formation, in relative depth format. 

Note: 

>Use the command “Plot Table” to see the log. x-axis is relative depth, ranging from 0 (formation top) to 
1 (formation bottom), y-axis log value 

Argument: 

1. formation name. Must exist in "Horizons" list (on slot "Geology") 
2. well name. Must exist in "Wells" list 
3. log name. Must exist in "Logs" list 


**:material-rhombus-split: plot_imported_logs_rDepth_add**(formation,log):  function to plot a given log (for all wells) in relative 
depth in a given formation 

Note:  
>Use command “Plot Table" to see the log. x-axis is relative depth, ranging from 0 (formation top) to 1 
(formation bottom), y-axis is log value 

Argument: 

1. formation name. Must exist in "Horizons" list (on slot "Geology") 
2. log name. Must exist in "Logs" list 


**:material-rhombus-split: plot_imported_logs_rDepth_remove**(formation,log): function to remove plots created by above 
function.  

Note: 
>Use this function to avoid generating unnecessary "Tables (graphs)" 

Argument: 

1. formation name. Must exist in "Horizons" list (on slot "Geology") 
2. log name. Must exist in "Logs" list

**:material-rhombus-split:plot_imported_log**(well,log) : plots an imported log vs TVDSS.  

Note: 

>Use FLAC3D command “Plot Table” to see the log. x-axis is TVDSS, y-axis is log value 

Argument: 

1. well name. Must exist in "Wells" list 
2. log name. Must exist in "Logs" list 