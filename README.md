# QGIS-USGS-TNM-Style-Template

This is my working draft to re-create USGS TNM Style Template for use in QGIS 3.x. The USGS Topo TNM Style Template is only avaialbe for ArcGIS, as a map document (MXD). There is nothing currently available for QGIS, so using the USGS's ArcGIS Style template as a reference I'm tryng to create a project template with equivalent symbology for QGIS. This is still a working draft and I haven't done any labeling for the layers, yet.

See accompanying blog post, Tips for Creating ArcGIS-like Styles in QGIS: https://opengislab.com/blog/2019/2/5/tips-for-creating-arcgis-like-symbology-in-qgis

UPDATE 3/21/2019: Newly added USGSTNM.xml for importing into QGIS style manager. 
For more info, see blog post: https://opengislab.com/blog/2019/3/16/converting-esri-styles-to-qgis-styles-using-slyr


FILE USAGE INFO:
Access to both ArcGIS and QGIS may be needed for the style files to work properly in QGIS.I have ArcGIS 10.6.1 and QGIS 3.4.3 installed on my machine when I created the QML files, so I'm not sure if it will work in QGIS.

The QGIS project file, USGSTNM_Template_QGIS3_Draft.qgs can be use as a Project Template file. Copy this file into the project_templates folder (e.g. C:\Users\Stephanie\AppData\Roaming\QGIS\QGIS3\profiles\default\project_templates). Then open this qgs file in a text editor and find/replace old data path with new data path (e.g. your own GDB). See the blog post link above for reference on how to do this.

If using the QML files individually, please read the note below.
Notes on QML files for filtered data layers:
The QML files that contain filtered data may not pull in the query used, so you may need to apply the querries below for these layers.
Right click on the layername >> Properties >> Source >> Provider Feature Filter.

For TNMDerivedNames Layer - apply the query below
GAZ_NAME IS NOT NULL AND 
((GAZ_NAME) NOT LIKE '%HISTORICAL%')

For Structures layer - apply the query below
((FCODE = 73002 OR FCODE = 73003 OR FCODE = 73004 OR FCODE = 73005 OR FCODE = 73006) AND SOURCE_ORIGINATOR LIKE '%Oak Ridge%') OR FCODE = 74026 OR FCODE = 80012 OR FCODE = 78000 OR FCODE=83006 OR FCODE = 78006 OR FCODE = 82010 OR ( FCODE = 74034 AND NAME LIKE '%Police%') OR FCODE = 74036

For Structure_GNIS layer - apply the query below
((GAZ_FEATURECLASS = 'Cemetery' AND (GAZ_NAME) NOT LIKE 'INDIAN%' AND (GAZ_NAME) NOT LIKE '%INDIAN%') OR GAZ_FEATURECLASS = 'Post Office') AND GAZ_NAME IS NOT NULL AND (GAZ_NAME) NOT LIKE '%HISTORICAL%'

Link to USGS Topo TNM Style Template: https://viewer.nationalmap.gov/tools/topotemplate/

