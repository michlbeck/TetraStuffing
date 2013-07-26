# Makefile for TetraMeshTools library
# Author: Dennis Luebke, 2012-08-31

# source files
dirSrc:= src
dirTrimesh2:= trimesh2
# local headers
incDir:= include
# local headers
ttmDir:= include/TetraMeshTools

outputDir:= lib
outputName:= libTetraMeshTools

CFLAGS:=        -O2 -pipe 
#CFLAGS+=        -fopenmp
#CFLAGS+=       -g
#CFLAGS+=       -O0
CFLAGS+=        -I$(incDir)
CFLAGS+=		-I$(ttmDir)
CFLAGS+=		-I$(dirTrimesh2)/include
CFLAGS+=        -fpic
#CFLAGS+=        -shared 

CXXFLAGS:=      $(CFLAGS)

srcs:= $(wildcard $(dirSrc)/*.cpp) $(wildcard $(dirTrimesh2)/src/*.cc)
objs:= $(srcs:.cpp=.o)
objs:= $(objs:.cc=.o)

# make targets
all: shared

shared:
	mkdir -p $(outputDir)
	$(CXX) $(CXXFLAGS) -shared $(dirSrc)/*.cpp $(dirTrimesh2)/src/* -o $(outputDir)/$(outputName).so

static: $(objs)
	mkdir -p $(outputDir)
	$(AR) rs $(outputDir)/$(outputName).a $(objs)
	
clean:
	rm $(objs)
	rm -rf $(outputDir)/*
