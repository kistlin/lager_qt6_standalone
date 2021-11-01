find_package(Qt6 6.2 COMPONENTS Core REQUIRED)

set(CMAKE_AUTOMOC ON)

set(SOURCES
        item.cpp
        qmodel.cpp
        )

add_library(component-lib-snake
        ${SOURCES}
        )

target_include_directories(component-lib-snake PUBLIC .)
target_include_directories(component-lib-snake PUBLIC ${PROJECT_SOURCE_DIR}/lib/immer)
target_include_directories(component-lib-snake PUBLIC ${PROJECT_SOURCE_DIR}/lib/lager)
target_include_directories(component-lib-snake PUBLIC ${PROJECT_SOURCE_DIR}/lib/zug)
target_link_libraries(component-lib-snake PRIVATE Qt6::Core)
