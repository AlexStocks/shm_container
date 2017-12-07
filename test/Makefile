NEED_GTESTX := 1
NEED_GFLAGS := 1
include /usr/local/gtestx/Makefile.env
include /usr/local/gtest/Makefile.env
include /usr/local/gflags/Makefile.env

CXX := /data/gcc-build-4.8.1/bin/g++
CXXFLAGS += -Wall -g -O2 -Wall -std=c++0x -fno-strict-aliasing -DUNIT_TEST
CXXFLAGS += -I../src
LDFLAGS += -pthread -Wl,-dn $(addprefix -l,stdc++) -Wl,-dy -lrt

.PHONY: all clean

TARGET := test
SRC := $(wildcard *.cc)
OBJ := $(patsubst %.cc,%.o,${SRC})

all: ${TARGET}

${TARGET}: %: ${OBJ}
	${CXX} ${CXXFLAGS} -o $@ $^ ${LDFLAGS}

${OBJ}: %.o: %.cc
	${CXX} ${CXXFLAGS} -c -o $@ $<

clean:
	${RM} ${TARGET} ${OBJ}
