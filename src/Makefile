
CXXFLAGS = -std=c++11 -g3 -O0
SOURCES += $(shell find . -name "*.cpp")
OBJS = mill.pb.o
OBJS += $(SOURCES:.cpp=.o)

%.pb.cc: %.proto
	protoc --cpp_out=. $<

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c -o $@ $<

%.o: %.cc
	$(CXX) $(CXXFLAGS) -c -o $@ $<

gcoded: $(OBJS)
	g++ $(CXXFLAGS) -o gcoded $(OBJS) -lrt $(shell pkg-config --libs protobuf)

clean:
	rm -f *.o
	rm -f gcoded
	rm -f mill.pb.*