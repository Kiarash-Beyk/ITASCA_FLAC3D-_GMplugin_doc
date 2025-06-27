:material-rhombus-split: Import_Wells: imports all offset wells into model. 

Note:  

>- Offset wells must be listed in "FLAC3D/Horizon/FormationTops.csv" 
>- Well deviations must be available in xyz (TVDSS) format in "FLAC3D/Deviation/” folder  
>- Deviation file names must follow “wellNmae_traj.csv format “ 
>- Well names must be exactly similar to well names listed in "FLAC3D/Horizon/FormationTops.csv" 

Arguments: None 

**:material-rhombus-split: Import_Horizons**: Imports formation horizons into model 

Note:  

>- Formation names are taken from "FLAC3D/Horizon/FormationTops.csv" 
>- Formation horizons must be saved in “stl” format and saved in "FLAC3D/Horizon/” folder 
>- It imports all available horizons (stl) and skips the horizons for which a stl file does not exist 
>- Formation horizons stl files must have exact same name as in "FLAC3D/Horizon/FormationTops.csv" 
>- stl files must be saved in binary format

Argument: None 


**:material-rhombus-split: Horizon_adjust**(formation,max_zAdjust,search_rad,power): Function to adjust a formation horizon to 
well picks listed in "Horizon/FormationTops.csv" 

Note:  
This function can be used to enforce full match between imported horizons and well formation tops  

Argument: 

1. formation horizon name 
2. maximum vertical adjustment allowed by user (m for project in SI unit) 
3. lateral extent of adjustment (adjustment is gradual, from max at well to zero at this distance).  
4. exponent for IDW function. Range from 1-3. lower values=> smoother adjustment, higher value=> 
sharper adjustment closer to wells 

**:material-rhombus-split: Horizon_copy**(source_geom,target_geom,z_shift): function to create a formation horizon from an 
existing horizon by depth shift 
Note: None

Argument:  

1. Source geometry existing in model imported by “Import_Horizons” function or created later 
2. Target geometry created by this function uperation 
3. Vertical shift: positive for upward, negative for downward shift  



**:material-rhombus-split: import_faults**: function to import faults from "FLAC3D/Fault/” folder 

Note:  
>- Faults must be stored as stl surface files in the following format “faultName.stl” 
>- Same fault names will be assigned to the zones intersected by faults by “identify_fault_zones” function 
>- Faults can be converted to stl from xyz point cloud by Rhino CAD tool  
Argument: None  

**:material-rhombus-split: identify_fault_zones**: function to identify and mark FLAC3D zones intersected by faults.  

Note:  
>- This function must be called after mesh is built and finalized  
>- This function must be called after “import_faults” function call 

Argument: None 


**:material-rhombus-split: vertical_densifier**(formation,slot,max_Height): function to reduce zone height to less than a user-defined 
max zone height for a given formation on a given slot. 

Note:  
>- This function must be called after mesh is built and finalized 

Argument:

1. Target formation name (zone group name) for densification 
2. FLAC3D zone slot number on which target formation name is stored 
3. user-defined max height. Any zone with height equal or greater than this number will be densified until 
its height drops below this number 

**:material-rhombus-split: Zone_Count**: function to count number of zones in model. 

Note:  
>- Initializes “Zone_Count” variable in "FISH Global Symbols" table 
>- This function must be called after mesh is built and finalized 

Argument: None 



**:material-rhombus-split: condition_mesh_for_dataImport**: function to prepare mesh for data population.  

Note: 

>- Calculates formation thickness (saves on Zone Extra 2) 
>-  Calculates relative depth of zone centers with respect to formation top (ranging from 0 to 1) and saves 
on zone Extra 1 (not to be overwritten until after data population) 
>- Must be called before data population (both Kriging or IDW) 
>- Must be called after mesh is finalized (and before importing offset well logs) 
>- It works just on hexahedral elements – no tetrahedral zones 

Argument: None