cmake_minimum_required(VERSION 3.21.0)

project(TestGUITool
        VERSION 0.0
        DESCRIPTION "My test app for GUI applications"
        HOMEPAGE_URL "https://github.com/GloryOfNight/TestGUITool"
        LANGUAGES CXX C)

include(cmake/ProjectOptions.cmake)
include(cmake/Sanitizers.cmake)
include(cmake/PreventInSourceBuilds.cmake)

add_subdirectory(thirdparty)

add_executable(${PROJECT_NAME} "src/main.cxx")

target_link_libraries(${PROJECT_NAME} PRIVATE SDL3-static imgui-static)

enable_sanitizers(${PROJECT_NAME} 
                    ${ENABLE_SANITIZER_ADDRESS} 
                    ${ENABLE_SANITIZER_LEAK} 
                    ${ENABLE_SANITIZER_UNDEFINED} 
                    ${ENABLE_SANITIZER_THREAD} 
                    ${ENABLE_SANITIZER_MEMORY})

install(TARGETS ${PROJECT_NAME})