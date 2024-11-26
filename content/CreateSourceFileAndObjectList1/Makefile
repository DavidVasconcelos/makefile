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

DEBUG = 1

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic

CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = 

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
EXECUTABLE_NAME = mainDebug
else
CXXFLAGS += -O3
EXECUTABLE_NAME = mainRelease
endif

CXX_COMPILER_CALL = $(CXX) $(CXXFLAGS)

# Manual list
# CXX_OBJECTS = my_lib.o main.o
#
# build: $(CXX_OBJECTS)
# 	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)

# Wildcard
CXX_SOURCES = $(wildcard *.cc)
CXX_OBJECTS = $(patsubst %.cc, %.o, $(CXX_SOURCES))

build: $(CXX_OBJECTS)
	$(CXX_COMPILER_CALL) $(CXX_OBJECTS) $(LDFLAGS) -o $(EXECUTABLE_NAME)
	
main.o:
	$(CXX_COMPILER_CALL) -c main.cc -o main.o

my_lib.o:
	$(CXX_COMPILER_CALL) -c my_lib.cc -o my_lib.o

execute:
	./$(EXECUTABLE_NAME)

# clean is often used as a target that removes the output of other targets
clean:
	rm -f $(CXX_OBJECTS)
	rm -f $(EXECUTABLE_NAME)

##############
## PATTERNS ##
##############
# $@: the file name of the target
# $<: the name of the first dependency
# $^: the names of all prerequisites
%.o: %.cc
	$(CXX_COMPILER_CALL) -c $< -o $@

# Example
#main.o: main.cc
#	$(CXX_COMPILER_CALL) -c main.cc -o main.o
