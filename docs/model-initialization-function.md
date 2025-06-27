**:material-rhombus-split: apply_stress_boundary_all_sides**: Function to apply zone stresses to all boundary zone faces (sides and 
top/bottom) for initial equilibrium 

Note: 
>"Zone face skin" must have been called before a call to this function. Model boundaries must be saved 
as "Top","Bottom","East","West","North" and "South" on slot "Boundary" for this function to work    

Argument: None 


**:material-rhombus-split: apply_stress_boundary_lateral**: Function to apply zone stresses to model lateral boundaries (just sides – 
as opposed to above function) for initial equilibrium  

Note :
>"Zone face skin" must have been called before a call to this function. Model boundaries must be saved 
as “East","West","North" and "South" on slot "Boundary" for this function to work 

Argument: None 

**:material-rhombus-split: horizontal_stress_from_pStr**(zone_pnt,Shmin,SHmax,SHmax_azimuth): Function to calculate and assign 
zone stress tensor to each zone using Shmin, SHmax and SHmax azimuth.  

Note: 
> - should be called for each zone (use it in a loop structure) 

 Argument:

1.  pointer to zone 
2.  Shmin magnitude 
3. SHmax magnitude 
4. SHmax azimuth (positive from north CW) 

Next four functions are inquiry functions, which can be useful after model initialization 

**:material-rhombus-split: plot_F3D_log_forAddedWell**(well,log_para,depthInterval,export_flag): Function to plot or export a log 
value (must exist in "Logs" list) for a non-offset well

Note : 
> - This function operates on non-offset wells only (wells added to model using "add_well" function) 
> - User can chose to export the log (to "Output/" folder) or just generate FLAC3D plot 

 Argument:

1. Well name: must exist in "added_Wells" list 
2. log name to be plotted/exported: must exist in "Logs" list 
3. Depth interval (sampling interval) for log plot/export 
4. Log export flag. "YES" enforces log export. Any other entry will do nothing 



**:material-rhombus-split: plot_F3D_stress**(well,stress_comp,depthInterval,export_flag): Function to plot or export a stress 
component 

Note: 
>Works for all wells existing in model, either on "Wells" or "added_Wells" list 
User can choose to export stress profile (to "Output/" folder) 

Argument: 

1. Well name: must exist in "added_Wells" or "Wells" list 
2. stress component to be plotted (valid entries are: xx, yy, zz, maximum, minimum, intermediate) 
3. Depth interval (sampling interval) for log plot/export 
4. Log export flag. "YES" enforces log export. Any other entry will do nothing 

**:material-rhombus-split: plot_F3D_zpressure**(well,depthInterval,export_flag): Function to plot or export zone pressure 

Note: 
>Works for all wells existing in model, either on "Wells" or "added_Wells" list 
User can choose to export pressure profile (to "Output/" folder) 

Argument: 
1. Well name: must exist in "added_Wells" or "Wells" list 
2. Depth interval (sampling interval) for log plot/export 
3. Log export flag. "YES" enforces log export. Any other entry will do nothing 

**:material-rhombus-split: Export_F3D_StrPress_MD**(well,depthInterval): Function to export stress components (min/int/max) and 
pressure from FLAC3D zones 

Note: 
 > - Works for all wells existing in model, either on "Wells" or "added_Wells"  

Argument:

1. Well name: must exist in "added_Wells" or "Wells" list 
2. Depth interval for log plot/export 