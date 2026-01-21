cmake_minimum_required(VERSION 3.20)

# 1. 修正：语言必须开启 CXX (C++)，否则用不了 Qt
project(PatientsManage LANGUAGES CXX)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

# 2. 修正：必须先告诉 CMake 你的 Qt 在哪，然后再去找包
# 注意：路径最后的斜杠我去掉了，保持整洁
set(CMAKE_PREFIX_PATH "D:/QQQT/6.7.3/mingw_64")

find_package(Qt6 COMPONENTS Core Gui Widgets REQUIRED)

# 3. 修正：源文件必须是 .cpp！请务必去重命名文件！
add_executable(PatientsManage
        Src/main.cpp
        Inc/main.h
)

# 4. 修正：这里必须填你的项目名 PatientsManage，不能填 untitled1
target_link_libraries(PatientsManage PRIVATE
        Qt::Core
        Qt::Gui
        Qt::Widgets
)

# 那些复杂的 DLL 复制脚本先删掉，CLion 运行调试不需要那些
# 以后打包发布时用 windeployqt 工具更方便