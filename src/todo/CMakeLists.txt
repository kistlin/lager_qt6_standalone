set(CMAKE_DEPENDS_USE_COMPILER ON)  # CLion fix

add_subdirectory(lib)

find_package(Qt6 6.2 COMPONENTS Gui REQUIRED)
find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)
find_package(Qt6 6.2 COMPONENTS QuickControls2 REQUIRED)
find_package(Qt6 6.2 COMPONENTS Widgets REQUIRED)
find_package(Qt6 6.2 COMPONENTS Concurrent REQUIRED)

set(CMAKE_AUTOMOC ON)

qt_add_executable(${PROJECT_NAME}_todo
        main.cpp
        )
qt_add_qml_module(${PROJECT_NAME}_todo
        VERSION 1.0
        URI qml
        QML_FILES
            main.qml
        SOURCES
            main.cpp
        )

target_link_libraries(${PROJECT_NAME}_todo PRIVATE component-lib-todo)
target_link_libraries(${PROJECT_NAME}_todo PRIVATE Qt6::Gui)
target_link_libraries(${PROJECT_NAME}_todo PRIVATE Qt6::Quick)
target_link_libraries(${PROJECT_NAME}_todo PRIVATE Qt6::QuickControls2)
target_link_libraries(${PROJECT_NAME}_todo PRIVATE Qt6::Widgets)
target_link_libraries(${PROJECT_NAME}_todo PRIVATE Qt6::Concurrent)
target_compile_definitions(${PROJECT_NAME}_todo PRIVATE LAGER_QML_DIR="${CMAKE_SOURCE_DIR}/src/todo")
