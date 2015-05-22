visitESSI
=========

A VisIt plugin that reads ESSI (HDF5) output. For what follows `$(VISIT_DIR)` is the directory where the visit tarball and install script are installed.

Compiles with VisIt 2.8.1 on Ubuntu 14.04, with `gcc-4.9`. Do a regular install of VisIt. I use the flags:

	./build_visit2_8_1 --required --hdf5 --makeflags "-j 16"

Once visit compiles without errors (and you can execute the visit executable), then go into

	cd $(VISIT_DIR)/visit2.8.1/visit2.8.1/src/databases
	git clone https://github.com/jaabell/visitESSI.git
	cd visitESSI
	../../bin/xml2cmake -clobber visitESSI.xml
	cd ..
	
Now you should be in `$(VISIT_DIR)/visit2.8.1/visit2.8.1/src/databases` again. There you need to edit
the CMakeLists.txt file to add the `visitESSI` plugin to the list of plugins that depend on HDF5. I put mine just under the line that reads:

	ENDIF(NOT XDMF_FOUND)
	CHECK_THIRDPARTY_DEPENDENT_PLUGINS(HDF5
	visitESSI
	AMR

Once that is done, go one level up (`$(VISIT_DIR)/visit2.8.1/visit2.8.1/src/`) and type

	cmake .
	make -j $(nprocs)
	
Wher `$(nprocs)` is the number of processes you wish yo use.

If all goes well, VisIt should be aware of plugin and be able to open `.h5.feioutput` files.


---
[UCD CompGeoMech](http://sokocalo.engr.ucdavis.edu/~jeremic/)

Created by: [Jose Abell](www.joseabell.com)

Last update to this timestamp: Thu 21 May 2015 18:26:00 PDT
