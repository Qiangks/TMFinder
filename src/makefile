CC = g++
CFLAGS = -O4 -Wall
INCS = -Ibliss-0.73

objects = main.o events.o edges.o tsubgraph.o subnets.o binner.h motif.o progress_counter.o bin_limits.o

all: bliss tmf

.PHONY: bliss tmf

bliss:
	@echo "build the bliss for tmf"
	$(MAKE) -C bliss-0.73

tmf: $(objects)
	mkdir -p ../bin
	${CC} ${CFLAGS} -o  ../bin/tmf main.o tsubgraph.o subnets.o events.o edges.o motif.o progress_counter.o bin_limits.o -lstdc++  -Lbliss-0.73/ -lbliss

main.o: events.o tsubgraph.o main.cc subnets.o
	${CC} ${CFLAGS} ${INCS} -c main.cc

tsubgraph.o: tsubgraph.h tsubgraph.cc 
	${CC} ${CFLAGS} ${INCS} -c tsubgraph.cc

events.o: events.h events.cc
	${CC} ${CFLAGS} ${INCS} -c events.cc

edges.o: edges.h edges.cc
	${CC} ${CFLAGS} ${INCS} -c edges.cc

subnets.o: subnets.h subnets.cc
	${CC} ${CFLAGS} ${INCS} -c subnets.cc

bin_limits.o: bin_limits.h bin_limits.cc
	${CC} ${CFLAGS} ${INCS} -c bin_limits.cc

motif.o: motif.h motif.cc
	${CC} ${CFLAGS} ${INCS} -c motif.cc

progress_counter.o: progress_counter.h progress_counter.cc
	${CC} ${CFLAGS} ${INCS} -c progress_counter.cc

clean:
	rm -f ../bin/tmf *.o
	cd bliss-0.73 && make clean
