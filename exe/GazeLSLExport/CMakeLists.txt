#TBB library
include_directories(${TBB_ROOT_DIR}/include)

# Local libraries
include_directories(${LandmarkDetector_SOURCE_DIR}/include)
	
include_directories(../../lib/local/LandmarkDetector/include)

# LSL
INCLUDE_DIRECTORIES(../../lib/3rdParty/lsl/include)

# FIXME: handle multiple platforms
set(LSL_LIB_DIR ${CMAKE_BINARY_DIR}/../lib/3rdParty/lsl/lib/x64/)
LINK_DIRECTORIES(${LSL_LIB_DIR})


add_executable(GazeLSLExport GazeLSLExport.cpp)
target_link_libraries(GazeLSLExport LandmarkDetector)
target_link_libraries(GazeLSLExport dlib)
TARGET_LINK_LIBRARIES(GazeLSLExport lsl)

target_link_libraries(GazeLSLExport ${OpenCV_LIBS} ${Boost_LIBRARIES} ${TBB_LIBRARIES} ${BLAS_LIBRARIES})

install (TARGETS GazeLSLExport DESTINATION bin)
