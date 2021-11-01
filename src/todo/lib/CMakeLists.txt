find_package(Qt6 6.2 COMPONENTS Core REQUIRED)

set(CMAKE_AUTOMOC ON)

set(SOURCES
        todo.cpp
        )

add_library(component-lib-todo
        ${SOURCES}
        )

target_include_directories(component-lib-todo PUBLIC .)
target_include_directories(component-lib-todo PUBLIC ${PROJECT_SOURCE_DIR}/lib/immer)
target_include_directories(component-lib-todo PUBLIC ${PROJECT_SOURCE_DIR}/lib/lager)
target_include_directories(component-lib-todo PUBLIC ${PROJECT_SOURCE_DIR}/lib/zug)
target_link_libraries(component-lib-todo PRIVATE Qt6::Core)
