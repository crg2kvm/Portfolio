CXX = g++
CXXFLAGS = -Wall  -pedantic -Og -g -std=c++17 -fsanitize=address -fsanitize=undefined -D_GLIBCXX_DEBUG
#-Werror
all: msh

msh: main.o
	$(CXX) $(CXXFLAGS) -o $@ $^

clean:
	rm -f *.o msh

test: msh
	python3 shell_test.py

SUBMIT_FILENAME=shell-$(shell date +%Y%m%d%H%M%S).tar.gz

archive:
	tar "--exclude=*.tgz" --exclude=msh --exclude=.git "--exclude=*.o" -zcvf $(SUBMIT_FILENAME) *
	@echo "Created $(SUBMIT_FILENAME); please upload and submit this file."

submit: archive

.PHONY: clean all test archive submit
