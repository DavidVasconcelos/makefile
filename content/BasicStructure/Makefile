# TARGETS
###############
## TARGETS   ##
###############
# target: prerequisites
#	commands

# The commands are a series of steps typically to make the target,
# 	need to start with a tab character, not space
# The prerequisites are file names, separated by spaces.
# 	These files need to exist before the commands for the target are run.

build: my_lib.o main.o
	g++ main.o my_lib.o -o main

main.o:
	g++ -c main.cc -o main.o

my_lib.o:
	g++ -c my_lib.cc -o my_lib.o

execute:
	./main

# clean is often used as a target that removes the output of other targets
clean:
	rm -f *.o
	rm -f main