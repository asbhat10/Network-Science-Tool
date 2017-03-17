CONTENTS OF THIS FILE
---------------------
   
 * Introduction
 * Installation


INTRODUCTION
------------


Today there are many kind of disasters like Tsunami, Hurricane, Floods etc. Every disaster may affect the connectivity of networks. Thus, networks built need to be robust to faults. Also as network might be over a vast area it is difficult to test the robustness of the network. In this project, we build a tool that helps us estimate the impact of such disasters(fault). 

In this project we consider a wired network as a undirected graph G(V,E) where V is the number of nodes and E is the no of Edges. We define the connectivity of a graph as the number of faults up to which the graph remains connected i.e. the number of connected components in G is one [1]. So, suppose the connectivity of a graph is k, then it can tolerate up to k-1 faults which implies that the graph remains connected even after k-1 faults. These faults can be confined in a region. Also, the faults do not give any information regarding the impact on the graph like the number of connected components into which it disintegrates, size of largest connected component, the locations where the impact of the fault is the highest etc. when the size of the fault is greater that the connectivity of the network.

To understand different types of faults and their impacts we introduce the concept of region based connectivity. In region based connectivity the fault is confined to a region. A region can be defined as a subgraph of diameter d (where diameter is the maximum of the shortest path distance taken between all pairs of nodes in the graph). A region can also be defined as a circle of radius ‘r’ [1]. We can see that there can be infinite number of circles of radius r in a network.  But as stated in paper [2], we can say that considering only a finite number of regions is sufficient to analyze a network. This project consists of tools that build and analyze faults in a network.



INSTALLATION
------------
I.	Installed Python 3.5.2 using the following commands

$ sudo apt-get update 
$ sudo apt-get install python3
$ apt-cache show python3
$ sudo apt-get install python3==3.5.2 

II.	Installed Django Framework with virtual environment using following commands

$ pip install virtualenv
$ virtualenv –python=python3 foaproject
$ source foaproject/bin/activate
$ pip install Django==1.10.2
$ Django-admin --version

III.	Installing Geospatial libraries
GEOS : GEOS is a C++ library for performing geometric operations, and is the default internal geometry representation used by GeoDjango (it’s behind the “lazy” geometries)[8].
Steps :
	$ wget http://download.osgeo.org/geos/geos-3.4.2.tar.bz2
	$ tar xjf geos-3.6.0.tar.bz2
	$ cd geos-3.6.0
	$ ./configure
	$ make
	$ sudo make install
	$ cd ..

PROJ.4 : It is a library for converting geospatial data to different coordinate reference systems[8].

Steps :
$ wget http://download.osgeo.org/proj/proj-4.9.1.tar.gz
$ wget http://download.osgeo.org/proj/proj-datumgrid-1.5.tar.gz
$ tar xzf proj-4.9.1.tar.gz
$ cd proj-4.9.1/nad
$ tar xzf ../../proj-datumgrid-1.5.tar.gz
$ cd ..
$ ./configure
$ make
$ sudo make install
$ cd ..

GDAL :  It is an excellent open source geospatial library that has support for reading most vector and raster spatial data formats[8].

Steps :
$ wget http://download.osgeo.org/gdal/1.11.2/gdal-1.11.2.tar.gz
$ tar xzf gdal-1.11.2.tar.gz
$ cd gdal-1.11.2
$ ./configure
$ make
$ sudo make install
$ cd ..

IV.	Installed PostgreSQL with PostGIS extension

Steps :
$ sudo add-apt-repository "deb http://apt.postgresql.org/pub/repos/apt/xenial-pgdg main"
$ wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | $ sudo apt-key add -
$ sudo apt-get update
$ sudo apt-get install postgresql-9.6

Adding PostGIS Extension to the PostgreSQL DB :
	
	$ wget http://download.osgeo.org/postgis/source/postgis-2.1.8.tar.gz
	$ tar xfz postgis-2.1.8.tar.gz
	$ cd postgis-2.1.8
$ ./configure
$ make
$ sudo make install
$ sudo ldconfig
$ sudo make comments-install
$ sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/shp2pgsql
$ sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/pgsql2shp
$ sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/raster2pgsql
$ psql -h localhost -U cse551foa nsrtp
nsrtp=# CREATE EXTENSION postgis;
nsrtp=# \q




