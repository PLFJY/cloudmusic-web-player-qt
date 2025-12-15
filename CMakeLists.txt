cmake_minimum_required(VERSION 3.19)
project(CloudMusicWebPlayer-Qt LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# Find Qt modules
find_package(Qt6 REQUIRED COMPONENTS Core Gui Widgets WebEngineWidgets)

qt_standard_project_setup()

qt_add_executable(CloudMusicWebPlayer-Qt
        main.cpp
)

set_target_properties(CloudMusicWebPlayer-Qt PROPERTIES
        OUTPUT_NAME "cloudmusic-web-player-qt"
        AUTOMOC ON
)

target_link_libraries(CloudMusicWebPlayer-Qt PRIVATE
        Qt6::Core
        Qt6::Gui
        Qt6::Widgets
        Qt6::WebEngineWidgets
)

set(ICON_SRC "${CMAKE_CURRENT_SOURCE_DIR}/favicon.png")

if (EXISTS "${ICON_SRC}")
    add_custom_command(TARGET CloudMusicWebPlayer-Qt POST_BUILD
            COMMAND ${CMAKE_COMMAND} -E copy_if_different
            "${ICON_SRC}"
            "$<TARGET_FILE_DIR:CloudMusicWebPlayer-Qt>/favicon.png"
            COMMENT "Copying favicon.png to output directory"
    )
else ()
    message(WARNING "Icon not found: ${ICON_SRC}. Place favicon.png next to main.cpp/CMakeLists.txt if you want it copied.")
endif ()