#--------------------------------------------------------------------
project(contour-tree)

#--------------------------------------------------------------------

# Add header files
set(HEADER_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/constants.h
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/ContourTree.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/ContourTreeData.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/DisjointSets.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/Grid3D.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/HyperVolume.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/MergeTree.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/Persistence.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/ScalarFunction.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/SimFunction.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/SimplifyCT.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/TopologicalFeatures.hpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/TriMesh.hpp
)
ivw_group("Header Files" ${HEADER_FILES})

#--------------------------------------------------------------------
# Add source files
set(SOURCE_FILES
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/ContourTree.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/ContourTreeData.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/HyperVolume.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/MergeTree.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/Persistence.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/SimplifyCT.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/TopologicalFeatures.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree/TriMesh.cpp
)
ivw_group("Source Files" ${SOURCE_FILES})

#--------------------------------------------------------------------
# Create library
add_library(contour-tree STATIC ${SOURCE_FILES} ${HEADER_FILES})
add_library(inviwo::contour-tree ALIAS contour-tree)

target_include_directories(contour-tree PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/ContourTree)
target_include_directories(contour-tree INTERFACE ${CMAKE_CURRENT_SOURCE_DIR})

#--------------------------------------------------------------------
# Define defintions
ivw_define_standard_definitions(contour-tree contour-tree)
ivw_define_standard_properties(contour-tree)

#--------------------------------------------------------------------
# Creates VS folder structure
ivw_folder(contour-tree ext)

#--------------------------------------------------------------------
# Make package (for other projects to find)
ivw_default_install_comp_targets(core contour-tree)
ivw_make_package(ContourTree contour-tree)

ivw_suppress_compiler_warnings(contour-tree)