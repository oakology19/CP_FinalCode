More information on the use of all the R scripts and toolboxes can be found in Appendix A of the Island Oak Consevation Plan by Sofie McComb and Claire Powers.

MaxEnt.7z:
Zipped file containing the MaxEnt toolbox. Unzip the file and open the toolbox with its various models in ArcGIS.
 The MaxEnt toolbox developed lists the models in the order they should be run: 1) Extent, 2) Oaks, 3) Island, and 4) Climate. 
  Detailed descriptions and figures of the pre-MaxEnt processing of data layers and all potential input environmental layers into MaxEnt are listed in Appendix A1-A2. 
   In general, environmental layers from each island were projected to NAD 83 California Teale Albers (Meters), masked to the same extent, resampled to 100 meters resolution, and written to an ASCII files. 
    An oak point csv was created from oak presence points, detailing the species and the projected coordinates.  

VegetationMapGrouping.Rmd:
This R Markdown script can be used to classify the broad island-by-island vegetation types into more specific vegetation classification schemes 
 that can be used to merge all the islands together and create a systematic raster of vegetation types to be inputted into MaxEnt.
	**DO NOT RUN THIS SCRIPT ALL AT ONCE**
		It is an interactive script where you need to input your selected vegetation classifications in the middle. 
		 In other words it makes an output halfway that needs to be corrected in excel on the basis of selected broad vegetation classification schemes (user decided),
			and then brought back in to make the final shapefile that is joined with the vegetation classification information.

KrigingCatalina_AllBCM.Rmd:
This R Markdown script can be used to interpolate the climate variables for Santa Catalina to the entire extent of the island,
 as the island is missing BCM climate data for some of its' extent. The island DEM was used for universal co-kriging.
  The model for loops through the climate layers for current climate and all future climate projections and time periods,
   and saves the interpolated climate layers in a new folder for input into the ArcGIS data processing model.
    The layers can be resampled to either cell size 10 or 100 meters (or other), which can be selected in the script.
     A big thanks to Allison Horst and her ESM 244 Data Analysis class for teaching us kriging.

BCM_Organization.Rmd:
This R Markdown script should be used to transfer the output files from the ArcGIS data processing model (MaxEnt Toolbox) to the MaxEnt input data files folders. 
 The script makes sure the files are sent to the correct folders, labeled the same across scenarios, and removes NaN issues for interpolated files.  
  The script is most useful to move climate layers as it automates the process, but it can be used for oak presence sample points,
   although it is faster to copy those over to just the historic samples folder.
    The script can be appended to do the same for the island layers features, but as we are currently not using those in the MaxEnt analysis
	 across all scenarios we have not included those in this script.

MaxEntAnalysisLooped.Rmd:
This R Markdown Script can be used to take the MaxEnt outputs and perform spatial and statistical analyses on the files for visualization in ArcGIS. 
 The only variable you have to change is the extent to the current scope of analysis being run, 
  as well as add in any important AUC or binary threshold information for each scenario. 
   The script then for loops through all the current and projected climate file outputs for the scenario and
    performs the specified analyses for each and writes the appropriate raster tiff files to the correct folders. 
     The entire process is automated so that a new scenario can be inputted and the all the same calculations and rasters can be created rapidly. 
      Then the files can just be visualized in ArcGIS using predesigned templates for each analysis type that we created.






