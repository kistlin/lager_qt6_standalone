# Standalone snake/todo example of lager
This is a copy of the snake and todo example from [1]. Few changes necessary to make it compile and work with Qt6 were made.

## Setup
### Get sources
Clone the repository.

Don't forget to fetch the submodules.
```
git submodule update --init
```

### Generate build files
In the root of the repository.
```
cmake -S . -B ./build
```

#### Snake
Build snake
```
cmake --build ./build --target lager_qt6_standalone_snake
```
Play snake
```
./build/src/snake/lager_qt6_standalone_snake
```

#### Todo
Build todo
```
cmake --build ./build --target lager_qt6_standalone_todo
```
Run todo
```
./build/src/snake/lager_qt6_standalone_todo
```

## Problems
### CLion
```
[ 39%] Built target lager_snake_qt6_standalone_automoc_json_extraction
make[3]: *** No rule to make target 'src/CMakeFiles/lager_snake_qt6_standalone.dir/compiler_depend.ts', needed by 'src/lager_snake_qt6_standalone_qmltyperegistrations.cpp'.  Stop.
make[2]: *** [CMakeFiles/Makefile2:205: src/CMakeFiles/lager_snake_qt6_standalone.dir/all] Error 2
make[1]: *** [CMakeFiles/Makefile2:213: src/CMakeFiles/lager_snake_qt6_standalone.dir/rule] Error 2
make: *** [Makefile:163: lager_snake_qt6_standalone] Error 2
```
To fix this error in CLion add `set(CMAKE_DEPENDS_USE_COMPILER ON)` to the `CMakeLists.txt`.

This cannot be set in the CLion settings, because CLion sets this to `False` on the command line call after our definitions.

## Resources
[1] [lager](https://github.com/arximboldi/lager.git)  
[2] [Introduction to the QML CMake API](https://www.qt.io/blog/introduction-to-the-qml-cmake-api)  
[3] [QML Modules in Qt 6.2](https://www.qt.io/blog/qml-modules-in-qt-6.2)  
[4] [CLion bug (CMAKE_DEPENDS_USE_COMPILER)](https://youtrack.jetbrains.com/issue/CPP-25989)