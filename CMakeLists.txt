__cc_find(Boost)
__cc_find(Eigen)

set(ILIBS eigen boost_system boost_filesystem boost_iostreams )
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
			
__add_real_target(admesh lib SOURCE ${SRCS} 
								INC ${INCS} 
								LIB ${ILIBS}
								DEF ${DEFS}
								)		
				
if(CC_INSTALL_ADMESH)
	__install_directory_specif(${CMAKE_CURRENT_SOURCE_DIR}/ admesh)
endif()
