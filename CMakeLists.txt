cmake_minimum_required(VERSION 3.16)

project(Application_Recette VERSION 0.1 LANGUAGES CXX)

set(CMAKE_CXX_STANDARD_REQUIRED ON)

find_package(Qt6 6.4 REQUIRED COMPONENTS Quick)

qt_standard_project_setup()

qt_add_executable(appApplication_Recette
    src/main.cpp
)

qt_add_qml_module(appApplication_Recette
    URI Application_Recette
    VERSION 1.0
    QML_FILES
        src/qml/Main.qml
        src/qml/Recette.qml
)

# Qt for iOS sets MACOSX_BUNDLE_GUI_IDENTIFIER automatically since Qt 6.1.
# If you are developing for iOS or macOS you should consider setting an
# explicit, fixed bundle identifier manually though.
set_target_properties(appApplication_Recette PROPERTIES
#    MACOSX_BUNDLE_GUI_IDENTIFIER com.example.appApplication_Recette
    MACOSX_BUNDLE_BUNDLE_VERSION ${PROJECT_VERSION}
    MACOSX_BUNDLE_SHORT_VERSION_STRING ${PROJECT_VERSION_MAJOR}.${PROJECT_VERSION_MINOR}
    MACOSX_BUNDLE TRUE
    WIN32_EXECUTABLE TRUE
)

target_link_libraries(appApplication_Recette
    PRIVATE Qt6::Quick
)

include(GNUInstallDirs)
install(TARGETS appApplication_Recette
    BUNDLE DESTINATION .
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    RUNTIME DESTINATION ${CMAKE_INSTALL_BINDIR}
)
