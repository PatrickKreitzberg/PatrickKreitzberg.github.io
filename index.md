# Greenland 

## Table of contents:
1. [Introduction](#introduction)
2. [Dependencies](#dependencies)
3. [Data & Acknowledgements](#data)
4. Buttons
5. Run Model
6. Plot Data Along A Path


<a name="introduction"></a>
# INTRODUCTION
This was created by Patrick Kreitzberg and Dr. Jesse Johnson at the University of Montana.  The program is a tool to help create data profiles using a gui. yada yada  

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

<a name="data"></a>
# DATA AND ACKNOWLEDGEMENTS

[data dl link](https://umt.box.com/s/8nosww6t9q0vhdtcsdlh3tpee8g3b1sx)

    Velocity Data:

J. Mouginot

Jeremie Mouginot, Eric Rignot, Bernd Scheuchl, and Romain Millan, Comprehensive Annual Ice Sheet Velocity Mapping Using Landsat-8, Sentinel-1, and RADARSAT-2 Data, Remote Sensing  2017, 9(4), 364; doi:10.3390/rs9040364, http://www.mdpi.com/2072-4292/9/4/364

Department of Earth System Science, University of California, Irvine

    SMB, t2m Data:

Brice Noël  
Institute for Marine and Atmospheric Research (IMAU)  
Utrecht University

    Surface, bed, and thickness data:

Mathieu Morlighem

BedMachine Greenland

Department of Earth System Science, University of California Irvine

M. Morlighem, E. Rignot, J. Mouginot, H. Seroussi and E. Larour, Deeply incised submarine glacial valleys beneath the Greenland Ice Sheet, Nat. Geosci., 7, 418-422, 2014, doi:10.1038/ngeo2167, http://www.nature.com/ngeo/journal/vaop/ncurrent/full/ngeo2167.html
