# Makefile for SofaTetraStuffing library
# Author: Dennis Luebke, 2012-09-02

# source files
dirSrc:= src
# local headers
incDir:= include

# TetraMeshTools path
ttmDir:= ../TetraMeshTools
ttmLibDir:= $(ttmDir)/lib

# SOFA root dir (change to where your own SOFA instance is living)
sofaDir:= ../../../../../Sofa/Sofa
sofaLibDir:=$(sofaDir)/lib

outputDir:= lib
outputName:= libSofaTetraStuffing

CFLAGS:=        -O2 -pipe 
#CFLAGS+=        -fopenmp
#CFLAGS+=       -g
#CFLAGS+=       -O0
CFLAGS+=        -I$(incDir)
CFLAGS+=		-I$(ttmDir)/include -I$(ttmDir)/include/TetraMeshTools
CFLAGS+=		-I$(sofaDir)/modules -I$(sofaDir)/framework
CFLAGS+=		-I$ttmInclude
CFLAGS+=        -fpic
#CFLAGS+=        -shared 

CXXFLAGS:=      $(CFLAGS)

# TetraMeshTools lib path and files
ttmLibs:= -L$(ttmLibDir) -lTetraMeshTools

# SOFA lib path and files
sofaLibs:= -L$(sofaLibDir) -lsofa_misc -lsofa_component_misc -lsofacore

# make targets
all: shared

shared:
	mkdir -p $(outputDir)
	$(CXX) $(CXXFLAGS) -shared $(dirSrc)/* -o $(outputDir)/$(outputName).so $(sofaLibs) $(ttmLibs)

static:
	mkdir -p $(outputDir)
	$(CXX) $(CXXFLAGS) -c $(dirSrc)/* -o $(outputDir)/$(outputName).o
	$(AR) rvs $(outputDir)/$(outputName).a $(outputDir)/$(outputName).o

	
clean:
	rm -rf $(outputDir)/$(outputName)*

