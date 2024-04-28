# RISC-V IME set Specification

## Introduction
This is a matrix extension proposal under the RISC-V IME extension standard. It has the following features.

* Low lost
    - Reuse the vector registers and the related CSRs.

* Compatibility
    - Support VLEN of vector registers from 128 bit to 4096 bit
    - Almost binary portability

* Rich data types
    - Integer int4/int8/int16
    - float fp4/fp8/fp16/bf16

## Build
This project is built using AsciiDoctor (Ruby). You can build by using the Docker Image, [RISC-V Docs Base Container Image repository](https://github.com/riscv/riscv-docs-base-container-image).

You can build like this:

```
# pull the docker
docker pull riscvintl/riscv-docs-base-container-image:latest

# clone this project

# run the container
docker run -it -v $(pwd)/riscv-isa-manual:/build riscvintl/riscv-docs-base-container-image:latest /bin/bash

# within the container
cd ./build
make
```

## Contributing
If you would like to contribute to this documentation, please refer to the [Documentation Developer's Guide](https://github.com/riscv/docs-dev-guide).

## Acknowledgement
This project refers to[riscv-isa-manual](https://github.com/riscv/riscv-isa-manual) and [riscv-matrix-extension-spec](https://github.com/T-head-Semi/riscv-matrix-extension-spec?tab=readme-ov-file). Thanks a lot.
