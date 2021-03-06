<a name="top"></a>
# Greenland 

## Table of contents:
1. [Introduction](#introduction)
1. [Dependencies](#dependencies)
1. [Data](#data)
1. [Acknowledgements](#ack)
1. [Main UI Features](#uifeatures)
1. [Static Plot UI](#uistatic)
1. [Markers](#markers)
1. Run Model
1. Plot Data Along A Path
1. [To do](#todo)
1. [Detailed Docmentation](#docu)


<a name="introduction"></a>
# INTRODUCTION
This was created by Patrick Kreitzberg under the guidance of Dr. Jesse Johnson at the University of Montana.  The program is a tool to help create data profiles using a gui. yada yada  


[top](#top)
<a name="dependencies"></a>
# DEPENDENCIES

(Python 2.7)

[//]: # # Installing Parallel HDF5 (pHDF5)  
[//]: # Parallel HDF5 is not necessary but can greatly increase the speed of the program-especially on start up.  

[//]: # ## MPICH (Required for pHDF5)  
[//]: # * [Download](http://www.mpich.org/downloads/) and unpack  
[//]: # * Used mpich-3.2 as it was the stable release at the time.  Do not use Hydra, use the full dist.  
[//]: # * Because I used a fresh linux install I needed to update gcc compilers: apt-get install gcc g++   
[//]: # * Configure MPICH before install inside the mpich folder:  
[//]: # ```
[//]: # $ ./configure --enable-romio --enable-shared --with-device=ch3:sock --disable-fortran --prefix=/home/pat/packages/mpich_install/
[//]: # $ make   
[//]: # $ make check  
[//]: # $ make install  
[//]: # $ make install check  
[//]: # ```
[//]: # * Add mpicc to path by appending 'export PATH=/home/pat/packages/mpich_install/bin:$PATH' onto .bashrc file.    

[//]: # ## mpi4py (Required for pHDF5)   

[//]: # * Since it was clean install i must install python-dev so mpi4py can build  (fixes Python.h not found error)
[//]: # ```$ sudo apt-get install python-dev  ```
[//]: # * [I followed these directions which I will print below](http://mpi4py.scipy.org/docs/usrman/install.html)  
[//]: # * [Download the mpi4py distribution](https://pypi.python.org/pypi/mpi4py)  
[//]: # * Then unpack and cd into the directory. 
[//]: # * Not sure if necessary but I edited mpi.cfg file to include 
[//]: #     * mpi_dir = /home/pat/packages/mpich_install 
[//]: # * In terminal:
[//]: # ```
[//]: # $ python setup.py build --mpicc=/path/to/mpich/bin/mpicc  (must end in /bin/mpicc)  
[//]: # $ sudo python setup.py install  
[//]: # ```

[//]: # ## pHDF5  
[//]: # [Download files](https://support.hdfgroup.org/HDF5/release/obtain5.html)  
[//]: # [Followed instructions here](https://support.hdfgroup.org/ftp/HDF5/current/src/unpacked/release_docs/INSTALL_parallel)  
[//]: # Specifically:  
[//]: # ```
[//]: # $ CC=/home/pat/packages/mpich_install/bin/mpicc ./configure --enable-parallel --prefix=/home/pat/packages/hdf_install/  
[//]: # $ make  
[//]: # $ make check  
[//]: # ```
[//]: # * I did get an error in the testph5diff.sh test but this just tests error output against a saved text file so you can skip with make -i check.  Possibly the MPI gives a different error output than what HDF is looking for.
[//]: # ```
[//]: # $ make install  
[//]: # $ make install check 
[//]: # ```
[//]: # * Add to path by appending the following to the bashrc file
[//]: #  [//]: #    * export PATH=/home/pat/packages/hdf_install/bin:$PATH

[//]: # ## h5py (Required for pHDF5)  
[//]: # * (requires numpy, Cython, setuptools, and pkgconfig)  
[//]: # * [Download the tar](https://pypi.python.org/pypi/h5py/2.7.0)
[//]: # * Unzip and CD into directory in terminal
[//]: # ```
[//]: # $ export CC=mpicc  
[//]: # $ python setup.py configure --mpi --hdf5=/path/to/hdf5 
[//]: # $ python setup.py build
[//]: # $ sudo python setup.py install
[//]: # ```

[//]: # # Required whether using pHDF5 or not

### Fenics
```
sudo add-apt-repository ppa:fenics-packages/fenics  
sudo apt-get update  
sudo apt-get install --no-install-recommends fenics   
sudo apt-get dist-upgrade  
```

### PyLab  
```
sudo apt-get install python-numpy python-scipy python-matplotlib
```

### PyQtGraph  
```
sudo pip install pyqtgraph
```

### H5py (if didn't install with parallel HDF5)
```
sudo pip install h5py
```
### PyQt4  
(I don't think PyQt5 works with python 2.7)  
```
apt-cache search pyqt  
sudo apt-get install python-qt4  
```
    
### PyDistMesh
```
sudo pip install PyDistMesh
```
Reference:  
P.-O. Persson, G. Strang, A Simple Mesh Generator in MATLAB. SIAM Review, Volume 46 (2), pp. 329-345, June 2004  

[top](#top)
<a name="data"></a>
# DATA
(Place in ./data directory)  
All data is the dataset with all the underlying data.  It is an hdf5 file with the velocity, surface, bed etc. data as numpy arrays.  The currently available dataset have a larger resolution ~900m.  A larger dataset with 150m resolution will be available soon.

The colormap data file is also a hdf5 file but the data are 8bit length 3 RGB arrays.  There is a colormap for each of the underlying data sets.  The colormaps are full resolution so the file size is 2.5 GB.

[All data](https://umt.box.com/s/8nosww6t9q0vhdtcsdlh3tpee8g3b1sx)  
[Colormap data](https://umt.box.com/s/0lbko76deskxxmbgb7wqn8s50cza2h0f)

[top](#top)  
<a name="ack"></a>
# ACKNOWLEDGEMENTS
## Velocity Data:

J. Mouginot

Jeremie Mouginot, Eric Rignot, Bernd Scheuchl, and Romain Millan, Comprehensive Annual Ice Sheet Velocity Mapping Using Landsat-8, Sentinel-1, and RADARSAT-2 Data, Remote Sensing  2017, 9(4), 364; doi:10.3390/rs9040364, http://www.mdpi.com/2072-4292/9/4/364

Department of Earth System Science, University of California, Irvine

## SMB, t2m Data:

Brice Noël  
Institute for Marine and Atmospheric Research (IMAU)  
Utrecht University

## Surface, bed, and thickness data:

Mathieu Morlighem

BedMachine Greenland

Department of Earth System Science, University of California Irvine

M. Morlighem, E. Rignot, J. Mouginot, H. Seroussi and E. Larour, Deeply incised submarine glacial valleys beneath the Greenland Ice Sheet, Nat. Geosci., 7, 418-422, 2014, doi:10.1038/ngeo2167, http://www.nature.com/ngeo/journal/vaop/ncurrent/full/ngeo2167.html

[top](#top)  
<a name="uifeatures"></a>
# UI Features
![Image](http://www.patkreitzberg.com/gl.png)

1. __Colormap image with key__  
1. __Map drop down selection__  
* Used to select which map you want to see.
1. __Auto-correct marker position checkbox__  
* Attempts to correct the marker to place it into the center of an ice stream
1. __Instructions__
* Loads a pop up window with short instructions for running the program.
1. __Clear Points Button__
* Removes the markers from the program.
1. __Integrate (also available by shift+clicking a marker)__
* Provides an integrated velocity stream for the last marker put down (or which ever marker is clicked)
1. __Plot Path Button__
* Plots all the data along the profile in a pop-up window.  The window has a seperate GUI.
1. __Run Model Button__
* Run the 1d profile model on the selected path.
1. __High-res Interpolators Button__
* Select to load the full sized data set and create interpolators on the data.  This can take several minutes.
* High-res data set is 150m resolution
1. __Generate Mesh Button__
* Creates a new window with a graph to show the mesh and its own GUI.  Uses PyDistMesh package to create the mesh.
* Save the mesh to a custom directory.  This creates an .xml file for the mesh as well as <b>FIXME</b>

<a name="uistatic"></a>
# Static Plotter
![Image](https://umt.box.com/shared/static/zdboo7of47lk0lh156yv3mi65tfhimzj.png)

1. Spatial Resolution Input 
1. Plot Button
1. Check boxes for what data you want plotted.






[top](#top)  
<a name="markers"></a>
# Markers
The markers select your path along which data will be examined.  To mark a spot click on the map wherever.  Multiple clicks will create multiple spots which will automatically form a line between each successive marker.  
* <b>Create:</b> click on map.  
* <b>Remove:</b> ctrl + click on marker.  
* <b>Move:</b> click once on marker to pick it up then again to place it down.  
* <b>Integrate:</b> shift + click to create a line from the marker which follows the velocity flow.  
* <b>Snap:</b> move a marker near an integrate line then click when it snaps to line. 
# Marker attributes
* <b>cx, cy</b>  These are the coordinate in pixels on the visual map itself (cx is x coord of color map).
* <b>dx, dy</b>  These are the coordinate in the data files so the velocity nearest the marker is velocity.data[dy][dx] (may require taking floor of dx, dy.
* <b>px, py</b>  Projected coordinates of the marker.  In the coordinates defined by the 2D projection of the data.  The data interpolators are calibrated to use px, py.
* <b> lines </b> Graphic lines displayed on map heading from previous marker, to the next one. lines[0] comes from prev marker.
* <b> corss</b> Graphic lines displayed on map that form the X at the location of the marker.


[top](#top)
<a name="lines"></a>
# Lines  
Lines that flow along a velocity path can be created by holding shift and clicking on a marker.  
* Ctrl + click on line deletes line

[top](#top)

<a name="todo"></a>
# TO DO
* <b>Antartic data</b>
    * <b>DONE</b> Email bryce noel about RACMO SMB and t2m datasets.
    * Find which papers to reference
* User script to create data file of certain resolution
* <b>SPEED</b>
    * up in any way (higher resolution data)
    * Hh5py in parallel? http://docs.h5py.org/en/latest/mpi.html
    * Auto-load smaller colormap with cmd line option for full
    * Quicker way to load image?
    * Main thread loads GUI and just velocity colormap
* Pick white integration path to graph/model
   * Move ends in and out
   * Pick line resolution
* Does each data need pathdistance--waste of memory?
* Add sliding parameters/changes to surface mass balance
* Check that it obeys the resolution input each time
* Change surface to being above the geoid not above average sea level
* Add checkbox to remove used colormaps from memory
* Smooth velocity width data
* Add more pictures to this site
* <b>MODEL</b>
    * Pause/play button for model run-back
* <b>STATIC PLOTTER</b>
    * Don't always create 3 plots.  Can do more or less
    * Right side panel max width
    * Could do 6 grid boxes with 5 plots and 1 for buttons 
* <b>BUGS</b>
    * Plot path, remove 'plot all' then click plot velocity width then plot -> crashes
    * Mesh can get a 'reduced to zero array' error -> find out how to trigger and fix/give instructions  
    * Each time velocity map loads it comes from RAM.  Each time bed map loads it comes from the SSD
* <b>CMD LINE</b>
    * Option to use low-res colormaps
    * Option to not use multiprocessing when loading interpolators
    
    
[top](#top)

<a name="docu"></a>
Classes:
1. [Colorbar]
1. [ColorbarAnchorWidget]
1. [Dataset]
1. [Instructions]
1. [InterpolateData]
1. [Marker]
1. [MeshGUI]
1. [ModelGUI]
1. [ModelPlotter]
1. [MyLegend]
1. [StaticPlotter]

Helper files:
1. [colorMaps]
1. [constancs]
1. [create_CM_datasets]
1. [data_functions]
1. [dataset_objects]
1. [gui]
1. [gui_functions]
1. [make_profile]
1. [math_functions]
1. [mesh_functions]
1. [pens]
1. [profile_driver]
1. [velocity_functions]


# Classes

## Colorbar  
Colorbar class is the colorbar/key for the maps.

## ColorbarAnchorWidget  
PyQtGraph object which keeps the colorbar stationary.

## Dataset  
Object that holds the data for each map.  FIXME add more


# Helper Files



