.PHONY: build test
build:
	cmake . -Bbuild
	cmake --build build

test: build
	cd build; ctest
