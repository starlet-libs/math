# Starlet Math

[![Tests](https://github.com/starlet-libs/math/actions/workflows/tests.yml/badge.svg)](https://github.com/starlet-libs/math/actions/workflows/tests.yml)
[![C++20](https://img.shields.io/badge/C%2B%2B-20-blue.svg)](https://isocpp.org/std/the-standard)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

A lightweight header-only math library for **Starlet** projects.

⚠️ **Note**
This is **NOT** intended to be a complete math library!
It's minimal and straightforward to make the math operations easier to understand and extend.
This makes it perfect for learning, experimentation, but not a drop-in replacement for full-fledged math libraries.

## Features

- Basic vector types: `Vec2`, `Vec3`, `Vec4`
- `Transform` struct for position, rotation, scale
- `Mat4` 4x4 matrix with:
    - Identity, transpose, inverse
    - Translation, rotation, scaling
    - `lookAt` and `perspective` helpers
    - Composition with `Transform`
- Constants and helpers:
    `pi`, `radians()`, `degrees()`
- **Starlet** Project Constants

## Prerequisites
- C++20 or later
- One of the following Build Systems,
    - CMake 3.20+
    - Meson 1.1+

## Using as a Dependency

### CMake
```cmake
include(FetchContent)

FetchContent_Declare(starlet_math
  GIT_REPOSITORY https://github.com/starlet-libs/math.git
  GIT_TAG main
)
FetchContent_MakeAvailable(starlet_math)

target_link_libraries(app_name PRIVATE starlet_math)
```

### Meson
> **Note:** Meson does not fetch dependencies automatically. Add the [`starlet_math.wrap`](./subprojects/starlet_math.wrap) file to your project's `subprojects` directory.

In your `meson.build`:

```python
starlet_math = subproject('starlet_math')
starlet_math_dep = starlet_math.get_variable('starlet_math_dep')
executable('app_name', 'main.cpp', dependencies: starlet_math_dep)
```

## Building and Testing
```bash
# 1. Clone starlet-math
git clone https://github.com/starlet-libs/math.git
cd starlet-math
```

### CMake
```bash
cmake -B build -DBUILD_TESTS=ON
cmake --build build
ctest --test-dir build
```

### Meson
```bash
meson setup build -Dbuild_tests=true
meson compile -C build
meson test -C build
```

## License
MIT License — see [LICENSE](./LICENSE) for details.
