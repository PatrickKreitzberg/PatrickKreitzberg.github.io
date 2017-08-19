## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/PatrickKreitzberg/PatrickKreitzberg.github.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/PatrickKreitzberg/PatrickKreitzberg.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# Greenland

run greenland.py

<ul class="posts">
    {% for post in site.posts %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>



https://umt.box.com/s/8nosww6t9q0vhdtcsdlh3tpee8g3b1sx

![Image](PatrickKreitzberg.github.io)


These are the dependencies.  I am using Python2.7

    INSTALL FENICS	

sudo add-apt-repository ppa:fenics-packages/fenics

sudo apt-get update

sudo apt-get install --no-install-recommends fenics

sudo apt-get dist-upgrade

    INSTALL PYLAB

sudo apt-get install python-numpy python-scipy python-matplotlib

    INSTALL PYQTGRAPH

sudo pip install pyqtgraph

    INSTALL h5py

sudo pip install h5py

    INSTALL pyqt4  (I don't think pyqt5 works with python 2.7)
    
    INSTALL PyDistMesh
sudo pip install PyDistMesh

apt-cache search pyqt

sudo apt-get install python-qt4

    ACKNOWLEDGEMENTS

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

