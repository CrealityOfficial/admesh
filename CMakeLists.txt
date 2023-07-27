__cc_find(Boost)
__cc_find(Eigen)

set(LIBS boost_system boost_filesystem boost_iostreams)
set(ILIBS eigen)
set(DEFS BOOST_ALL_NO_LIB BOOST_ALL_DYN_LINK)
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
								LIB ${LIBS}
								ILIB ${ILIBS}
								DEF ${DEFS}
								INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}
								)		
				
if(CC_INSTALL_ADMESH)
	__install_directory_specif(${CMAKE_CURRENT_SOURCE_DIR}/ admesh)
endif()
