set(CMAKE_DEPENDS_USE_COMPILER ON)  # CLion fix

add_subdirectory(lib)

find_package(Qt6 6.2 COMPONENTS Gui REQUIRED)
find_package(Qt6 6.2 COMPONENTS Quick REQUIRED)
find_package(Qt6 6.2 COMPONENTS QuickControls2 REQUIRED)
find_package(Qt6 6.2 COMPONENTS Widgets REQUIRED)
find_package(Qt6 6.2 COMPONENTS Concurrent REQUIRED)

set(CMAKE_AUTOMOC ON)

qt_add_executable(${PROJECT_NAME}
        main.cpp
        )
qt_add_qml_module(${PROJECT_NAME}
        VERSION 1.0
        URI qml
        QML_FILES
            main.qml
        )

target_link_libraries(${PROJECT_NAME} PRIVATE component-lib)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Gui)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Quick)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::QuickControls2)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Widgets)
target_link_libraries(${PROJECT_NAME} PRIVATE Qt6::Concurrent)
target_compile_definitions(${PROJECT_NAME} PRIVATE LAGER_QML_DIR="${CMAKE_SOURCE_DIR}/src")
