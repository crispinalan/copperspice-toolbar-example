set(CS_VERSION 1.7)

list(APPEND test_INCLUDES    
    ${CMAKE_CURRENT_SOURCE_DIR}/mainwindow.h
   
    
   
    
)

list(APPEND test_SOURCES
    ${CMAKE_CURRENT_SOURCE_DIR}/main.cpp
    ${CMAKE_CURRENT_SOURCE_DIR}/mainwindow.cpp      
    ${CMAKE_CURRENT_SOURCE_DIR}/mainwindow.ui    

   #qrc_speak.cpp
  
)
# use copperspice resource macro generates a call to the appropriate resource compiler
# run rcc to generate qrc output
#COPPERSPICE_RESOURCES(   
   #${CMAKE_CURRENT_SOURCE_DIR}/../speak.qrc
   
#)



# run uic to generate source
COPPERSPICE_RESOURCES(
    ${CMAKE_CURRENT_SOURCE_DIR}/mainwindow.ui  
    
)

add_executable(test ${test_SOURCES})

target_include_directories(test PRIVATE ${CMAKE_SOURCE_DIR}/src)

target_link_libraries(test

    
    CopperSpice::CsCore
    CopperSpice::CsGui
    #CopperSpice::CsMultimedia   

)


if(CMAKE_SYSTEM_NAME MATCHES "(Linux|OpenBSD|FreeBSD|NetBSD|DragonFly)")
set_target_properties(test PROPERTIES OUTPUT_NAME test)
endif()

install(TARGETS test DESTINATION .)

# Copy the libraries and plugins necessary for the application to the install path

#these are defined: copperspice/cmake/CopperSpiceDeploy.cmake

# linux only
cs_copy_library(CsCore)
cs_copy_library(CsGui)
#cs_copy_plugins(CsMultimedia)












