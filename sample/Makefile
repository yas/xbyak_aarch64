SRC=add.cpp add2.cpp label.cpp direct_write.cpp dump.cpp bf.cpp
OBJ=$(SRC:.cpp=.o)
DEP=$(SRC:.cpp=.d)
EXE=$(SRC:.cpp=.exe)
all: $(EXE)

LDFLAGS=-L ../lib -lxbyak_aarch64
CFLAGS=-std=c++11 -g -DNDEBUG -Wall -Wextra -I ../
ifneq ($(DEBUG),1)
CFLAGS+=-O2
endif

%.o: %.cpp
	$(CXX) -c $< -o $@ $(CFLAGS) -MMD -MP -MF $(@:.o=.d)

-include $(DEP)

%.exe: %.o
	$(CXX) $< -o $@ $(LDFLAGS)

clean:
	rm -rf $(EXE) $(OBJ) $(DEP)

.PHONY: clean

.SECONDARY: $(OBJ)
