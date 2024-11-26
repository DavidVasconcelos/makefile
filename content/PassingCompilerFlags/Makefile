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
EXECUTABLE_NAME = main

CXX_STANDARD = c++17
CXX_WARNINGS = -Wall -Wextra -Wpedantic

CXX = g++
CXXFLAGS = $(CXX_WARNINGS) -std=$(CXX_STANDARD)
LDFLAGS = 

ifeq ($(DEBUG), 1)
CXXFLAGS += -g -O0
else
CXXFLAGS += -O3
endif

COMPILER_CALL = $(CXX) $(CXXFLAGS)


build: my_lib.o main.o
	$(COMPILER_CALL) main.o my_lib.o -o $(EXECUTABLE_NAME)
	
main.o:
	$(COMPILER_CALL) -c main.cc -o main.o

my_lib.o:
	$(COMPILER_CALL) -c my_lib.cc -o my_lib.o

execute:
	./main

# clean is often used as a target that removes the output of other targets
clean:
	rm -f *.o
	rm -f main
