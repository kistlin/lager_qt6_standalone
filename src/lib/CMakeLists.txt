find_package(Qt6 6.2 COMPONENTS Core REQUIRED)

set(CMAKE_AUTOMOC ON)

set(SOURCES
        model.cpp
        qmodel.cpp
        )

add_library(component-lib
        ${SOURCES}
        )

target_include_directories(component-lib PUBLIC .)
target_include_directories(component-lib PUBLIC ${PROJECT_SOURCE_DIR}/lib/immer)
target_include_directories(component-lib PUBLIC ${PROJECT_SOURCE_DIR}/lib/lager)
target_include_directories(component-lib PUBLIC ${PROJECT_SOURCE_DIR}/lib/zug)
target_link_libraries(component-lib PRIVATE Qt6::Core)
