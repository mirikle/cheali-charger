
include(${CMAKE_SOURCE_DIR}/src/core/CMakeLists.txt)

set(THIS_FILE_PATH ${CMAKE_SOURCE_DIR}/src/hardware/imaxB6-generic/)

set(IMAXB6_SOURCE
    imaxB6.cpp
    imaxB6.h
    imaxB6-pins.h
    TimerOne.cpp
    TimerOne.h
    SMPS_PID.h
    SMPS_PID.cpp
    adc.cpp
    adc.h
)

set (IMAXB6_SOURCE_FILES "")
foreach (SOURCE ${IMAXB6_SOURCE})
    set(THIS_FILE THIS_FILE-NOTFOUND)
    find_file(THIS_FILE ${SOURCE} PATHS ${THIS_FILE_PATH} NO_DEFAULT_PATH)
#    message("append ${THIS_FILE}, ${SOURCE}")
    list (APPEND IMAXB6_SOURCE_FILES ${THIS_FILE})
endforeach()

include_directories(${THIS_FILE_PATH})

SET(ALL_SOURCE_FILES
    ${SOURCE_FILES}
    ${IMAXB6_SOURCE_FILES}
    ${CORE_SOURCE_FILES}
)

include(${CMAKE_SOURCE_DIR}/src/core/CMakeListsPost.txt)
