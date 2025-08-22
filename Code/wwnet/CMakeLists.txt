set(WWNET_SRC
    BWBalance.cpp
    BWBalance.h
    connect.cpp
    connect.h
    fromaddress.h
    msgstat.cpp
    msgstat.h
    msgstatlist.cpp
    msgstatlist.h
    msgstatlistgroup.cpp
    msgstatlistgroup.h
    netstats.cpp
    netstats.h
    netutil.cpp
    netutil.h
    networkobject.cpp
    networkobject.h
    networkobjectfactory.cpp
    networkobjectfactory.h
    networkobjectfactorymgr.cpp
    networkobjectfactorymgr.h
    networkobjectmgr.cpp
    networkobjectmgr.h
    packetmgr.cpp
    packetmgr.h
    packettype.h
    rhost.cpp
    rhost.h
    singlepl.cpp
    singlepl.h
    wwpacket.cpp
    wwpacket.h
    network-typedefs.h
    socket_wrapper.h
)

# Targets to build.
add_library(wwnet STATIC)

target_link_libraries(wwnet PRIVATE
    wwcommon
)

target_sources(wwnet PRIVATE ${WWNET_SRC})

if (WIN32)
    target_sources(wwnet PRIVATE socket_wrapper_win32.cpp)
else()
    target_sources(wwnet PRIVATE socket_wrapper_posix.cpp)
endif()