#GRASS GIS 7 intro
<img style="float: right;" src="image/grass_symbol.png" width="100"/>
###Session Objectives
* Database structure of GRASS GIS
* About the course data set
* First steps in using GRASS GIS 7
 + the graphical user interface (GUI)
   - displaying raster and vector maps
   - querying maps
   - adding map elements
   - bmap swiping with two different Landsat coverages
   - bivariate scatterplots
 + GRASS GIS command structure
   - command line or GUI?
 + Creating a perspective view
___
___
##GRASS GIS Database concept:
![db](image/db.png)

___
###graphical view:
![db2](image/db_graphic.png)

… effectively a tree of subdirectories.

GRASS GIS is a multi-user system when storing “**grassdata**” on a network drive.
Users can share “**locations**” and manage therein own “**mapsets**“ for the data.

GRASS GIS will do the file management for you!
___
####Standard GIS formats versus GRASS 7 Database

|![db](image/dbl.png)|![db](image/dbr.png)|
| -------------         | ------------- |
|Data in **standard GIS** formats.|Data in **GRASS GIS** formats.|
|Store in directory:|Store in directory:|
|/home/user/**gisdata**/|/home/user/**grassdata**/|
|or a shared network directory|or a shared network directory|

___
##<span style="color:red">*Exercise*</span> - GRASS startup and first steps
![startup](image/startup.png)
![gui](image/gui.png)

___
###Displaying raster and vector maps
A) Using the **menu**
![menu](image/menu.png)

B) Using the **icons**
![display](image/display.png)

___
###Display the “roadsmajor” vector map
+ Load the “roadsmajor” vector map into the canvas, zoom to map if needed:
![dispvec](image/dispvec.png)
![toolbar](image/toolbar.png)

___
###Show vector map attributes
Open the attribute table of the “**roadsmajor**” vector map by
* … either right-mouse clicking in layer tree on map name
* … or using the related “Show Attribute table” icon
![attribute](image/attribute.png)

___
###SQL queries of attributes
Select the **single lane roads** in the “**roadsmajor**” vector map
+ Use “Simple” SQL query
+ The selected vectors will be highlighted in the map display
![sql](image/sql.png)





###Adding map elements
![addmap](image/addmap.png)

___
###Modify element settings and position
Using the Wake county “**elevation**” and “**roadsmajor**” maps:

![pointer](image/pointer.png)

Use **pointer** to
- move map elements
- edit element settings with  a click

___
###Map histogram tool
![histo](image/histo.png)


___

###Adding a Lat-Long grid to the map
Using the NC state “**elev_state_500m**” map:
![latlong](image/latlong.png)
**Select a grid size in grid unts (here: LL – 1 deg)	→ 	Draw grid as LatLong WGS84 grid**

![latlong_img](image/latlong_img.png)

___

###Map swiping for multitemporal maps
Load the LANDSAT 5 (1987) and 7 (2002) **RGB composites** of Wake county:
![rgb](image/rgb.png)

###Convenient map selector
Load the LANDSAT **channels red and green** using the convenient map selector
![mapselector](image/mapselector.png)


___
###Bivariate Scatterplots
Load the LANDSAT 7 2002 channels 1 and 3 of Wake county.
![biva](image/biva.png)

___
___
##<span style="color:red">*Overview*</span>: GRASS GIS command structure
![overview](image/overview.png)

<span style="color:green">*Ninja Trick*</span>, type the desired prefix (e.g. v.) and then <tab><tab> to complete the command name

___
###GRASS startup and first steps
**Know where you are...**

get projection information for the North Carolina Location

command: ``` g.proj ```

  
        wxGUI: Settings → Map projections → Manage projections
![wxgui](image/wxgui.png)
<img style="float: right;" src="image/gproj.png" width="200"/>

get projection information for the North Carolina sample data set:


|type | name|description|
| -------------| ------------- |
|name       :| Lambert Conformal Conic |Projection name|
|proj       : |lcc| projection|
|datum      :| nad83|geodetic datum|
|a          :|6378137.0| ellipsoid GR80|
|es         :| 0.006694380022900787|ellipsoid GR80|
|lat_1      :| 36.16666666666666|standard parallels|
|lat_2      :| 34.33333333333334|standard parallels|
|lat_0      :| 33.75|reference latitude|
|lon_0      :| -79|reference longitude|
|x_0        :| 609601.22|} lon and lat shifts... |
|y_0        :| 0|...(false easting/northing)|
|units      :| meters| unit |

##GRASS Database concept - Projection
Projection of the North Carolina Location:
+ **NAD83(HARN) / North Carolina – EPSG code: 3358**
![projection](image/projection.png)

+proj=lcc

+lat_1=36.16666666666666 +lat_2=34.33333333333334 

+lat_0=33.75 +lon_0=-79

+x_0=609601.22 +y_0=0

+ellps=GRS80 +units=m +no_defs

___
###Graphical user interface versus Command line
+ GRASS GIS offers a graphical user interface



+ On command line, there is (text) help:
    
        r.univar --help



   * There are flags (e.g. -g ) and parameters (e.g. map= )



+ From command line, you can open the module's GUI (just call the command without parameters)

        r.univar --ui

+ … or generate a Python script template

       r.univar --script

**STYLE**: Menu: Settings → GUI Settings → Appearance → Module dialog style: Basic top/left
![guivs](image/guivs.png)
The graphical user interface effectively generates the respective command for the command line (and also writes to the shell “history”)

___
####Command line at its best
**Advantages of the command line**

<img style="float: right;" src="image/cmdl.png" width="400"/>

+ Run “history” to see all your previous commands, “forever”

+ History is stored individually per MAPSET (note that the history of each map is stored within the map's metadata, for this use r|r3|v.info)

+ Search in history with CTRL-R

+ Save it to a file:

``` history > my_protocol.sh``` 

<img style="float: right;" src="image/script.png" width="350"/>

+ Note for Windows users: no history command but
```  “Command console” tab → “Log file”``` 
+ Polish protocol file, use “# comment” to annotate it

+ Rerun such a protocol file in a later GRASS GIS session with 

``` sh my_protocol.sh ```

Note: a simplified command line is included in the graphical user interface, tab “Command console”.

It offers a “Command prompt protocol” button.


+ These script will work for decades...
___
##<span style="color:red">*Exercise*</span> Perspective view
Load the Wake county “elevation” map (this tool requires OpenGL support):

![perspective](image/perspective.png)




