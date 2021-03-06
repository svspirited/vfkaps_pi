##---------------------------------------------------------------------------
## Author:      Rasbats aka. Mike Rossiter
## Copyright:
## License:     wxWidgets License
##---------------------------------------------------------------------------

# define minimum cmake version
CMAKE_MINIMUM_REQUIRED(VERSION 2.6.2)

PROJECT(vfkaps_pi)

SET(PACKAGE_NAME vfkaps_pi)
SET(VERBOSE_NAME vfkaps)
SET(TITLE_NAME vfkaps)
SET(CPACK_PACKAGE_CONTACT "Mike Rossiter")

SET(VERSION_MAJOR "2")
SET(VERSION_MINOR "1.1")

SET(NAME_SUFFIX "ov50")

set (CMAKE_CXX_STANDARD 11)

#SET(CMAKE_BUILD_TYPE Debug)
SET( wxWidgets_USE_DEBUG OFF)
SET( wxWidgets_USE_UNICODE ON)
SET( wxWidgets_USE_UNIVERSAL OFF)
SET( wxWidgets_USE_STATIC OFF)

#SET(CMAKE_BUILD_TYPE Debug)
OPTION(VFKAPS_USE_SVG "Use SVG graphics" ON)

INCLUDE("cmake/PluginConfigure.cmake")

IF(VFKAPS_USE_SVG)
  ADD_DEFINITIONS(-DVFKAPS_USE_SVG)
ENDIF(VFKAPS_USE_SVG)


SET(SRC_vfkaps
        	src/vfkaps_pi.h
        	src/vfkaps_pi.cpp
        	src/icons.h
        	src/icons.cpp
			src/vfkapsgui.h
	    	src/vfkapsgui.cpp
	    	src/vfkapsgui_impl.cpp
	    	src/vfkapsgui_impl.h
	    	src/vfkapsOverlayFactory.cpp
        	src/vfkapsOverlayFactory.h
	    	src/ocpn_plugin.h
			src/tinyxml.cpp
			src/tinyxml.h
			src/tinyxmlerror.cpp
			src/tinyxmlparser.cpp

        	src/wxJSON/jsonval.cpp
        	src/wxJSON/jsonreader.cpp
			src/wxJSON/jsonwriter.cpp
		
			src/wx/json_defs.h
			src/wx/jsonval.h
        	src/wx/jsonreader.h
			src/wx/jsonwriter.h
	)


ADD_LIBRARY(${PACKAGE_NAME} SHARED ${SRC_vfkaps})

ADD_DEFINITIONS(-DTIXML_USE_STL)

INCLUDE("cmake/PluginInstall.cmake")
INCLUDE("cmake/PluginLocalization.cmake")
INCLUDE("cmake/PluginPackage.cmake")
