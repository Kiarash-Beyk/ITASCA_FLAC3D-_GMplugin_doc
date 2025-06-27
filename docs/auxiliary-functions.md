Functions in this section can be used to make model adjustments. 

**:material-rhombus-split: add_well**(wname,fname_): function to add a single well trajectory (none offset well) 

Note: 

> - Wells imported by this function are added to “added_Wells” list and are just for data visualization and inquiry

> - These wells are not included in data interpolation, so no need to import logs for these wells 

Argument:

1. user-defined well name 
2. well trajectory file name. Well trajectory file format must follow x,y,TVDSS (CSV file) and stored in 
"Deviation" folder 

**:material-rhombus-split: topography_isoDept**: Function to generate depth contours on formation horizon surfaces 

Note: 
>TVDSS is stored on geometry node extra 2 
Argument: None 

**:material-rhombus-split: formation_element_cnt**: counts number of zones in each formation in model and list it in command 
window. No export to file 

Note: None 

Argument: None 

**:material-rhombus-split: geom_node_expor**(formation): function to export a formation horizon as xyz points. Can be used to 
generate synthetic horizons by manipulation in Rhino.

Note: 

>Exports to "Output/formation_Top_xyz_F3D.csv" 

Argument:

1. Formation name as in “Horizons” list 


  
**:material-rhombus-split: Shmin_SHmax_azimuth**(extra1,extra2,extra3): Function to loop through all zones and calculate and save 
Shmin, SHmax and SHmax azimuth (+CW from North), and store in user-defined zone extras 

Note: None 

Argument:   

1. zone extra number (integer) for Shmin 
2. zone extra number (integer) for SHmax 
3. zone extra number (integer) for SHmax azimuth (+CW)



**:material-rhombus-split: license_check**: reports days left on 3D Geomechanics Plug-in.  

Note:  
>- Type in the following command in FLAC3D command line to execute the function: “@license_check”. 
- Project set up functionalities do not work on an expired license. The data interpretation and export 
utilities still remain functional

Argument:  None