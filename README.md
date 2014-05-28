visitESSI
=========

A VisIt plugin that reads ESSI (HDF5) output

Compiles with VisIt 2.7.2 on Ubuntu 13.10. Please download binary distribution of VisIt
[here](https://wci.llnl.gov/codes/visit/executables.html). Don't forget the install script! Do a
regular install of VisIt. 

Once that is done, compile visitESSI by doing

	xml2cmake -clobber visitESSI.xml
	cmake -DCMAKE_BUILD_TYPE:STRING=Debug
	make

If all goes well, plugin shared libraries are placed in
`$(HOME)/.visit/2.7.2/linux-x86_64/plugins/databases/`. Generated libraries are:

* `libEvisitESSIDatabase_ser.so`
* `libIvisitESSIDatabase.so`
* `libMvisitESSIDatabase.so`

VisIt should be aware of plugin and be able to open `.feioutput` files.


---

Jose Abell
Wed 28 May 2014 04:55:32 PM PDT