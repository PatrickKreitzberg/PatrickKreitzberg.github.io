# Greenland 

## Table of contents:
1. [Introduction](#introduction)
2. [Dependencies](#dependencies)
3. [Data](#data)
4. [Acknowledgements](#ack)
5. [UI Features](#uifeatures)
6. [Markers](#markers)
7. Run Model
8. Plot Data Along A Path


<a name="introduction"></a>
# INTRODUCTION
This was created by Patrick Kreitzberg under the guidance of Dr. Jesse Johnson at the University of Montana.  The program is a tool to help create data profiles using a gui. yada yada  

![Image](http://www.patkreitzberg.com/gl.png)

<a name="dependencies"></a>
# DEPENDENCIES

(Python 2.7)

### Fenics

sudo add-apt-repository ppa:fenics-packages/fenics  
sudo apt-get update  
sudo apt-get install --no-install-recommends fenics   
sudo apt-get dist-upgrade  

### PyLab  
sudo apt-get install python-numpy python-scipy python-matplotlib

### PyQtGraph  
sudo pip install pyqtgraph

### H5py  
sudo pip install h5py

### PyQt4  
(I don't think PyQt5 works with python 2.7)  
apt-cache search pyqt  
sudo apt-get install python-qt4
    
### PyDistMesh
sudo pip install PyDistMesh  
P.-O. Persson, G. Strang, A Simple Mesh Generator in MATLAB. SIAM Review, Volume 46 (2), pp. 329-345, June 2004   

<a name="data"></a>
# DATA
(Place in ./data directory)  
All data is the dataset with all the underlying data.  It is an hdf5 file with the velocity, surface, bed etc. data as numpy arrays.  The currently available dataset have a larger resolution ~900m.  A larger dataset with 150m resolution will be available soon.

The colormap data file is also a hdf5 file but the data are 8bit length 3 RGB arrays.  There is a colormap for each of the underlying data sets.  The colormaps are full resolution so the file size is 2.5 GB.

[All data](https://umt.box.com/s/8nosww6t9q0vhdtcsdlh3tpee8g3b1sx)  
[Colormap data](https://umt.box.com/s/0lbko76deskxxmbgb7wqn8s50cza2h0f)

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

<a name="markers"></a>
# Markers
The markers select your path along which data will be examined.  To mark a spot click on the map wherever.  Multiple clicks will create multiple spots which will automatically form a line between each successive marker.  
* <b>Create:</b> click on map.  
* <b>Remove:</b> ctrl + click on marker.  
* <b>Move:</b> click once on marker to pick it up then again to place it down.  
* <b>Integrate:</b> shift + click to create a line from the marker which follows the velocity flow.  
* <b>Snap:</b> move a marker near an integrate line then click when it snaps to line.  


<a name="uifeatures"></a>
# UI Features

1. Colormap image with key
    






