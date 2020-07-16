cmake_minimum_required(VERSION 3.5)

#project name
project(Boost_Demo)


set(Boost_USE_STATIC_LIBS        ON) # only find static libs
set(Boost_USE_MULTITHREADED      ON)
set(Boost_USE_STATIC_RUNTIME    OFF)
set(Boost_NO_SYSTEM_PATHS		 ON)
set(Boost_DEBUG ON) #
#set(Boost_ARCHITECTURE "-x64") 
#set(Boost_THREADAPI "win64") 
set(BOOST_INCLUDEDIR "D:/CDS_projects/CATARC/git-catarc/_library/includes/boost/v1.61.0/include")
set(BOOST_LIBRARYDIR "D:/CDS_projects/CATARC/git-catarc/_library/win_x64/boost/v1.61.0/lib")


find_package(Boost 1.61.0 REQUIRED COMPONENTS	
			 serialization
)


if(Boost_FOUND)

	#add the executable
	add_executable(Boost_Serialization 
					src/example.cpp
					src/point_2d.h
					)
	
    target_include_directories(Boost_Serialization
		PRIVATE
			src
		PUBLIC
			${Boost_INCLUDE_DIRS}
		)
		
	target_include_directories(Boost_Serialization PUBLIC
                           "${PROJECT_BINARY_DIR}"
                           )	
	

	target_link_libraries(Boost_Serialization 
		PRIVATE
			Boost::serialization
        )

endif()
			



#specify the c++ standard
#set(CMAKE_CXX_STANDARD 11)
#set(CMAKE_CXX_STANDARD_REQUIRED True)

