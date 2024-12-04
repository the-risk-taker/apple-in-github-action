cmake_minimum_required(VERSION 3.20)

project(HelloWorld LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

find_package(Qt6 COMPONENTS Core Gui Qml Quick REQUIRED)

qt_standard_project_setup(REQUIRES 6.5)

qt_add_executable(HelloWorld
    main.cpp
)

qt_add_qml_module(HelloWorld
    URI Test
    VERSION 1.0
    QML_FILES
        Main.qml
)

target_link_libraries(HelloWorld PRIVATE
    Qt6::Quick
)

if (APPLE)
    set_target_properties(HelloWorld PROPERTIES
        MACOSX_BUNDLE TRUE
        MACOSX_BUNDLE_GUI_IDENTIFIER "com.example.HelloWorld"
        MACOSX_BUNDLE_BUNDLE_NAME "HelloWorld"
        MACOSX_BUNDLE_BUNDLE_VERSION "1.0"
        MACOSX_BUNDLE_SHORT_VERSION_STRING "1.0"
        XCODE_ATTRIBUTE_CODE_SIGN_IDENTITY "iPhone Developer"
        XCODE_ATTRIBUTE_DEVELOPMENT_TEAM "<Your Team ID>"
    )
endif()
