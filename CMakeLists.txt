__cc_find(Boost)
__cc_find(Eigen)

set(ILIBS eigen boost_system boost_filesystem boost_iostreams boost_log)
set(DEFS BOOST_ALL_NO_LIB)
set(SRCS    connect.cpp
			normals.cpp
			shared.cpp
			
			stl_io.cpp
			stlinit.cpp
			util.cpp)
			
set(INCS    stl.h
			${eigen_INCLUDE_DIRS}
			${BOOST_INCLUDE_DIRS}
			)
			
			
if(BUILD_ADMESH_STATIC)
	__add_real_target(admesh lib SOURCE ${SRCS} 
								INC ${INCS} 
								LIB ${ILIBS}
								DEF ${DEFS}
								)
else()
	__add_real_target(admesh dll SOURCE ${SRCS} 
								INC ${INCS} 
								LIB ${ILIBS}
								DEF ${DEFS}
								)
endif()			
				
if(CC_INSTALL_ADMESH)
	__install_directory_specif(${CMAKE_CURRENT_SOURCE_DIR}/ admesh)
endif()
