###############
## VARIABLES ##
###############
# Note: Variables can only be strings
# Note: Single or double quotes for variable names or values have no meaning to Make

# CC: Program for compiling C programs; default cc
# CXX: Program for compiling C++ programs; default g++
# CFLAGS: Extra flags to give to the C compiler
# CXXFLAGS: Extra flags to give to the C++ compiler
# CPPFLAGS: Extra flags to give to the C preprocessor
# LDFLAGS: Extra flags to give to the linker

INCLUDE_DIR = include
SOURCE_DIR = src
BUILD_DIR = build

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic

CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
CPPFLAGS = -I $(INCLUDE_DIR)
LDFLAGS = 

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
export EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O3
export EXECUTABLE_NAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS) $(CPPFLAGS)

# Manual list
# CXX_OBJECTS = my_lib.o main.o
#
# build: $(CXX_OBJECTS)
# 	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)

# Wildcard
CXX_SOURCES = $(wildcard $(SOURCE_DIR)/*.cc)
CXX_OBJECTS = $(patsubst $(SOURCE_DIR)/%.cc, $(BUILD_DIR)/%.o, $(CXX_SOURCES))
##############
## TARGETS ##
##############
create:
	mkdir -p $(BUILD_DIR)

build: create $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(BUILD_DIR)/$(EXECUTABLE_NAME)
	
main.o:
	$(CXX_COMPILER_CALL) -c main.cc -o main.o

my_lib.o:
	$(CXX_COMPILER_CALL) -c my_lib.cc -o my_lib.o

execute:
	./$(BUILD_DIR)/$(EXECUTABLE_NAME)

# clean is often used as a target that removes the output of other targets
clean:
	rm -rf $(BUILD_DIR)
	
##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the names of all prerequisites
$(BUILD_DIR)/%.o: $(SOURCE_DIR)/%.cc
	$(CXX_COMPILER_CALL) -c $< -o $@

# Example
#main.o: main.cc
#	$(CXX_COMPILER_CALL) -c main.cc -o main.o
