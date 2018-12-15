# rust-sfml-starter

This is a starter to use `SFML` with Rust.
In this project, we don't install SFML C (and C++) libraries to the root system (we are not using `sudo make install`, which is evil 😈).

This project is developped on MacOS, feel free to open PR to make it works on Linux too! ✨

# Summary
 - [First installation]()
 - [Development usage]()
 - [Release mode]()

## First install: dependencies
### Fetching dependencies
```sh
## create a vendors directory containing dependencies
mkdir vendors
cd vendors
## CSFML
git clone https://github.com/SFML/CSFML.git
cd CSFML
### - latest stable release
git checkout $(git describe --tags $(git rev-list --tags --max-count=1))
cd ..
## SFML
git clone https://github.com/SFML/SFML.git
cd SFML
### - latest stable release
git checkout $(git describe --tags $(git rev-list --tags --max-count=1))
cd ..
cd ..
```

### Building dependencies (C/C++)
```sh
## tells compiler where to find SFML and CSFML libs
export LIBRARY_PATH=$(pwd)/vendors/SFML/lib:$(pwd)/vendors/CSFML/lib
export LD_LIBRARY_PATH=${LIBRARY_PATH}
export DYLD_LIBRARY_PATH=${LIBRARY_PATH}

## BUILD
### - SFML
cd vendors/SFML
cmake .
make all
cd ..

### - CSFML
cd CSFML
export SFML_DIR="$(pwd -P)/../SFML"
cmake -DCMAKE_MODULE_PATH="$SFML_DIR/cmake" .
make all
cd ..
```

## How to dev
Make sure you installed your dependencies as described above, then:
```sh
export LIBRARY_PATH=$(pwd)/vendors/SFML/lib:$(pwd)/vendors/CSFML/lib
export LD_LIBRARY_PATH=${LIBRARY_PATH}
export DYLD_LIBRARY_PATH=${LIBRARY_PATH}
```

Finally: `cargo run`

That's it!
