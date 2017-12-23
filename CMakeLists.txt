CMAKE_MINIMUM_REQUIRED (VERSION 3.2.2)
PROJECT (Inotify)

SET (CMAKE_CXX_STANDARD 11)


ADD_SUBDIRECTORY (test)
ADD_SUBDIRECTORY (example)

ADD_LIBRARY (Inotify INTERFACE)
TARGET_INCLUDE_DIRECTORIES (Inotify INTERFACE ${CMAKE_CURRENT_SOURCE_DIR}/include)